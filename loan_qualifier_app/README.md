# Chris2Hedge, Challenge 2, Loan Qualified Application
Loan Qualifier Application to determine Maximum loan amounts, to income, various banks and interest rates
Just after the title, introduce your project by describing attractively what the project is about and what is the main problem that inspires you to create this project or what is the main contribution for the potential user of your project.

---

## Technologies
For this Challenge we will use Terminal, Visual Studio, Import functions for Excel CSV files, Path Library to refernce various files and library paths of data, and use Fire and Questionary
Describe the technologies required to use your project such as programming languages, libraries, frameworks, and operating systems. Be sure to include the specific versions of any critical dependencies that you have used in the stable version of your project.

---

## Installation Guide

In this section, you should include detailed installation notes containing code blocks and screenshots.
To begin: pip fire install, pip install questionary, 
from pathlib import Path

from qualifier.utils.fileio import load_csv, save_csv

from qualifier.utils.calculators import (
    calculate_monthly_debt_ratio,
    calculate_loan_to_value_ratio,
)
def load_csv(csvpath):
    
    """Reads the CSV file from path provided.

    Args:
        csvpath (Path): The csv file path.

    Returns:
        A list of lists that contains the rows of data from the CSV file.

    """
    with open(csvpath, "r") as csvfile:
        data = []
        csvreader = csv.reader(csvfile, delimiter=",")

        # Skip the CSV Header
        next(csvreader)

        # Read the CSV data
        for row in csvreader:
            data.append(row)
    return data

csvpath = questionary.text("~Desktop/Berkeley_Fintech_Bootcamp/Starter_Code_2/loan_qualifier_app/daily_rate_sheet.csv").ask()
    csvpath = Path(csvpath)
    if not csvpath.exists():
        sys.exit(f"Oops! Can't find this path: {csvpath}")

    return load_csv(csvpath)

def save_csv(csvpath,data,header=None):
    with open(csvpath, "w", newline="") as csvfile:
        csvwriter = csv.writer(csvfile, delimiter=",")
        if header:
            csvwriter.writerow(header)
        csvwriter.writerows(data)



---

## Usage

This section should include screenshots, code blocks, or animations explaining how to use your project.
The User will type in persoanl info to see what bank loans, type, loan rates they qualify for, these will be in a new csv file output
---

## Contributors

In this section, list all the people who contribute to this project. You might want recruiters or potential collaborators to reach you, so include your contact email and, optionally, your LinkedIn or Twitter profile.
Fintech bootcamp tutor Aatari helped debug and finess my code, still havfe a few error I will check with the TA on during office hours
---

## License

When you share a project on a repository, especially a public one, it's important to choose the right license to specify what others can and can't with your source code and files. Use this section to include the license you want to use.
From the challenge 2 folder we used: qualifier function, fire and questiary, additional starter code provided in the challenge 2 starter file also was used: credit score, debt to income, loan to value and max loan size, calculators.py
Additiaonlly fileio.ap is where we wrote and mapped the csv write path for output of applicants loan applicaiton will write  anew csv file
