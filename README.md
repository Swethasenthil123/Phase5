# Phase5
{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "private_outputs": true,
      "provenance": []
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "source": [
        "**Data Source**"
      ],
      "metadata": {
        "id": "5u1elujXeHX7"
      }
    },
    {
      "cell_type": "code",
      "execution_count": null,
      "metadata": {
        "id": "ZOzr6i6Q_hGt"
      },
      "outputs": [],
      "source": [
        "import numpy as np\n",
        "import pandas as pd\n",
        "import matplotlib.pyplot as plt\n",
        "import seaborn as sns\n",
        "sns.set_style('whitegrid')\n",
        "%matplotlib inline"
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "data=pd.read_csv(\"USA_Housing.csv\")\n"
      ],
      "metadata": {
        "id": "RWlmc87V_xkt"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#understanding the data\n",
        "data.info()"
      ],
      "metadata": {
        "id": "gMYwLOXcCWcM"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Data pre processing**"
      ],
      "metadata": {
        "id": "Gj9tvUm2j-lF"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "data.head()"
      ],
      "metadata": {
        "id": "73SRRbWUCiTa"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "data.describe()"
      ],
      "metadata": {
        "id": "jRB9qOtnHLcq"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "**Feature selection**\n",
        "\n"
      ],
      "metadata": {
        "id": "tFCIDLPRey6B"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "USA_Housing=pd.read_csv('/content/USA_Housing.csv')\n",
        "sns.pairplot(USA_Housing)"
      ],
      "metadata": {
        "id": "wE_LgkXETZez"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "sns.distplot(USA_Housing['Price'],hist_kws=dict(edgecolor=\"black\", linewidth=1),color='Blue')"
      ],
      "metadata": {
        "id": "3rWMtdXRaEnY"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#Displaying correlation among all the columns\n",
        "USA_Housing.corr()"
      ],
      "metadata": {
        "id": "sXhxvFXcaLrP"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "sns.heatmap(USA_Housing.corr(), annot = True)"
      ],
      "metadata": {
        "id": "yZu9KgtXaWyw"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "training a linear regression model"
      ],
      "metadata": {
        "id": "m12hao02V-Bu"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#getting all column names\n",
        "USA_Housing.columns\n",
        "\n",
        "\n"
      ],
      "metadata": {
        "id": "vIuwMKMjVf9m"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Columns as Features\n",
        "X = USA_Housing[['Avg. Area Income', 'Avg. Area House Age', 'Avg. Area Number of Rooms',\n",
        "       'Avg. Area Number of Bedrooms', 'Area Population']]"
      ],
      "metadata": {
        "id": "tQFXvO0UYw1H"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# Price is my Target Variable, what we trying to predict\n",
        "y = USA_Housing['Price']"
      ],
      "metadata": {
        "id": "YFclpNlcWyYY"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "Model Training"
      ],
      "metadata": {
        "id": "2UkfOQ3pbfRN"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "from sklearn.model_selection import train_test_split\n",
        "X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=101)"
      ],
      "metadata": {
        "id": "B_nvSAg3biCT"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#importing the Linear Regression Algorithm\n",
        "from sklearn.linear_model import LinearRegression"
      ],
      "metadata": {
        "id": "KHG3yjTFb3N0"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#creating LinearRegression Object\n",
        "lm = LinearRegression()"
      ],
      "metadata": {
        "id": "N2_HDFlqb7PS"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#Training the Data Model\n",
        "lm.fit(X_train, y_train)"
      ],
      "metadata": {
        "id": "u8Hxt_Zsb-dp"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "markdown",
      "source": [
        "\n",
        "**Evaluation**"
      ],
      "metadata": {
        "id": "qC1p7EcecJaV"
      }
    },
    {
      "cell_type": "code",
      "source": [
        "#Displaying the Intercept\n",
        "print(lm.intercept_)"
      ],
      "metadata": {
        "id": "X0iI25qicTLk"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "coeff_data = pd.DataFrame(lm.coef_, X.columns, columns=['Coefficient'])\n",
        "coeff_data"
      ],
      "metadata": {
        "id": "1hch0DF8cNcP"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "#predictions\n",
        "predictions = lm.predict(X_test)"
      ],
      "metadata": {
        "id": "RhhuchdfcrKx"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "plt.scatter(y_test, predictions, edgecolor='black')"
      ],
      "metadata": {
        "id": "_eHOX7e-ctsT"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "sns.distplot((y_test - predictions), bins = 50, hist_kws=dict(edgecolor=\"black\", linewidth=1),color='Blue')"
      ],
      "metadata": {
        "id": "zWlLPulcc6II"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "from sklearn import metrics"
      ],
      "metadata": {
        "id": "diEMWB-xc_Bp"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "print('MAE:', metrics.mean_absolute_error(y_test, predictions))\n",
        "print('MSE:', metrics.mean_squared_error(y_test, predictions))\n",
        "print('RMSE:', np.sqrt(metrics.mean_squared_error(y_test, predictions)))"
      ],
      "metadata": {
        "id": "tkaCsfcgdAML"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
}
