# Swan UI

Running on [swan-carleton.github.io](swan-carleton.github.io).

## Maintainability

Almost all of the content of the page can be managed after deployment by modifying the `.json` files in the public repository.

### **Steps to modify the data mentioned below**

1. Clone the repository

        git clone https://github.com/swan-carleton/swan-carleton.github.io.git

2. Create a new branch for your changes

        git checkout -b <branch-name>

2. Modify the data you desire following the file structures and instructions below

3. Commit and push your changes. E.g.

        git commit -m "<your message>"

        git push -u origin <branch-name>

5. Submit a pull request your changes to be reviewed and merged.

### **Page Data**

Modifiable lab summary and research interest. Also latest lab news.

**Usage**

- To modify the summary and research interest, simply update the fields text under `/pageData/homePageData.json`.

- To update the news, insert a news object at the beginning of the `news` array under `/pageData/homePageData.json`.

- Commit your changes and submit a pull request

**Directories**

    /pageData/homePageData.json

**Fields**

    summary: String (required)
    researchInterest: String (required)
    news: Array of news objects (required)
        date: String (required)
        text: String (news content, required)

**Example**

    {
        "summary": "Some summary",
        "researchInterest": "Our research interest ...",
        "news": [
            {
                "date": "April 2, 2021",
                "text": "Good news!"
            },
            ...
        ]
    }

### **People**

Faculty members, current graduate students, undergraduate students and alumnis of the lab.

**Usage**

1. Upload the photos to `/peopleData/photos`.

2. Append information following the structure shown below to `index.json` file.

3. Commit your changes and submit a pull request.

**Diretories**

    /peopleData/index.json
    /peopleData/photos/

**Fields**

    Faculty: Object
        name: String (required)
        role: String (required)
        school: String (required)
        imgUrl: String (file path, optional)
        links: Array of link objects (optional)

    currentGraduate: Object
        name: String (required)
        program: String (required)
        school: String (required)
        imgUrl: String(file path, optional)
        links: Array of link objects (optional)

    currentUndergraduate: Object
        name: String (required)
        program: String (required)
        school: String (required)
        imgUrl: String(file path, optional)
        links: Array of link objects (optional)

    alumni: Object
        name: String (required)
        program: String (required)
        position: String (position & company, required)
        imgUrl: String(file path, optional)
        links: Array of link objects (optional)

        links: Array of link objects
            type: enum (linkedin, github, website, email) (required)
            link: String (link/email address) (required)

**Example**

Single Object to append

    {
        "name": "John Appleseed",
        "program": "Master of Science, 1998-2000",
        "school": "Some University",
        "imgUrl": "/peopleData/photos/johnAppleseed.png",
        "links": [
            {
                "type": "email",
                "link": "johnappleseed@mail.com"
            }
        ]
    }

Overview

    "faculty": [
        ...,
        {
            "name": "Olga Baysal",
            "role": "Associate Professor, Graduate Director",
            "school": "Carleton University",
            "imgUrl": "/peopleData/photos/olgabaysal.png",
            "links": [
                {
                    "type": "website",
                    "link": "http://olgabaysal.com"
                },
                {
                    "type": "email",
                    "link": "olga.baysal@carleton.ca"
                }
            ]
        }
    ],
    "currentGraduate": [
        ...,
        {
            "name": "Lance Wang",
            "program": "MCS-thesis Data Science, 2019-2021",
            "school": "Carleton University",
            "imgUrl": "/peopleData/photos/LanceWang.jpg",
            "links": [
                {
                    "type":"website",
                    "link":"https://lancewg.com/"
                }
            ]
        }
    ],
    "currentUndergraduate": [
        ...,
        {
            "name": "Yizhang Cao",
            "program": "UG-project, Winter 2021",
            "school": "Carleton University",
            "imgUrl": "/peopleData/photos/yizhangcao.jpg",
            "links": [
                {
                    "type": "github",
                    "link": "https://github.com/tigercao1"
                },
                {
                    "type": "linkedin",
                    "link": "https://www.linkedin.com/yizhang-tiger-cao"
                }
            ]
        }
    ],
    "alumni": [
        ...,
        {
            "name": "Davoud Saljoughi",
            "program": "MCS-thesis, 2020-2021",
            "position": "Analyst/Data Specialist, Health Canada",
            "links": []
        }
    ]

### **Publications**

Publications affiliated with the lab.

**Usage**

1. Upload the publication to `/publications/<folder>/`.

2. Upload a cover picture to `/publications/images/`.

3. Append information following the structure shown below to `index.json` file.

4. Commit your changes and submit a pull request.

**Directories**

    /publications/index.json
    /publications/pdfs/
    /publications/slides/
    /publications/<folder>/

`<folder>` can be any common types of the file groups for publications. pdfs and slides can be uploaded directly to existing folders.

**Fields**

    title: String (optional)
    authors: String (optional)
    conference: String (optional)
    summary: String (optional)
    imageUrl: String (optional)
    links: Array of link objects (optional)
        type: String (type of document, required)
        link: String (file path/url, required)

**Example**

Single Object to append

    {
        "title": "Some title",
        "authors": "John Appleseed and Sam the Brilliant",
        "conference": "In Proc. of the International conference on Mining Software Repositories (MSR), Madrid, Spain, May 17-19, 2021",
        "summary": "Some Summary",
        "imageUrl": "/publications/images/image.png",
        "links": [
            {
                "type": "pdf",
                "link": "/publications/pdfs/this_publication.pdf"
            },
            {
                "type": "slides",
                "link": "/publications/pdfs/this_slides.pptx"
            },
            {
                "type": "recording",
                "link": "https://youtube.com/some-video"
            }
        ]
    }

Overview

    [
        {
            "title": "Studying the Change Histories of Stack Overflow and GitHub Snippets",
            "authors": "Saraj Singh Manes and Olga Baysal",
            "conference": "In Proc. of the International conference on Mining Software Repositories (MSR), Madrid, Spain, May 17-19, 2021",
            "summary": "Some Summary",
            "imageUrl": "/publications/images/image.png",
            "links": [
                {
                    "type": "pdf",
                    "link": "/publications/pdfs/this_publication.pdf"
                },
                {
                    "type": "slides",
                    "link": "/publications/pdfs/this_slides.pptx"
                },
                {
                    "type": "recording",
                    "link": "https://youtube.com/some-video"
                }
            ]
        },
        ...
    ]