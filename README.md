# SkiTime

Welcome to sktime
A unified interface for machine learning with time series

🚀 Version 0.33.0 out now! Check out the release notes here.

sktime is a library for time series analysis in Python. It provides a unified interface for multiple time series learning tasks. Currently, this includes time series classification, regression, clustering, annotation, and forecasting. It comes with time series algorithms and scikit-learn compatible tools to build, tune and validate time series models.

Overview	
Open Source	BSD 3-clause
Tutorials	Binder !youtube
Community	!discord !slack
CI/CD	github-actions readthedocs platform
Code	!pypi !conda !python-versions !black
Downloads	PyPI - Downloads PyPI - Downloads Downloads
Citation	!zenodo
📚 Documentation
Documentation	
⭐ Tutorials	New to sktime? Here's everything you need to know!
📋 Binder Notebooks	Example notebooks to play with in your browser.
👩‍💻 Examples	How to use sktime and its features.
✂️ Extension Templates	How to build your own estimator using sktime's API.
🎛️ API Reference	The detailed reference for sktime's API.
📺 Video Tutorial	Our video tutorial from 2021 PyData Global.
🛠️ Changelog	Changes and version history.
🌳 Roadmap	sktime's software and community development plan.
📝 Related Software	A list of related software.
💬 Where to ask questions
Questions and feedback are extremely welcome! We strongly believe in the value of sharing help publicly, as it allows a wider audience to benefit from it.

Type	Platforms
🐛 Bug Reports	GitHub Issue Tracker
✨ Feature Requests & Ideas	GitHub Issue Tracker
👩‍💻 Usage Questions	GitHub Discussions · Stack Overflow
💬 General Discussion	GitHub Discussions
🏭 Contribution & Development	dev-chat channel · Discord
🌐 Meet-ups and collaboration sessions	Discord - Fridays 13 UTC, dev/meet-ups channel
💫 Features
Our objective is to enhance the interoperability and usability of the time series analysis ecosystem in its entirety. sktime provides a unified interface for distinct but related time series learning tasks. It features dedicated time series algorithms and tools for composite model building such as pipelining, ensembling, tuning, and reduction, empowering users to apply an algorithm designed for one task to another.

sktime also provides interfaces to related libraries, for example scikit-learn, statsmodels, tsfresh, PyOD, and fbprophet, among others.

Module	Status	Links
Forecasting	stable	Tutorial · API Reference · Extension Template
Time Series Classification	stable	Tutorial · API Reference · Extension Template
Time Series Regression	stable	API Reference
Transformations	stable	Tutorial · API Reference · Extension Template
Parameter fitting	maturing	API Reference · Extension Template
Time Series Clustering	maturing	API Reference · Extension Template
Time Series Distances/Kernels	maturing	Tutorial · API Reference · Extension Template
Time Series Alignment	experimental	API Reference · Extension Template
Annotation	experimental	Extension Template
Time Series Splitters	maturing	Extension Template
Distributions and simulation	experimental	
⏳ Install sktime
For troubleshooting and detailed installation instructions, see the documentation.

Operating system: macOS X · Linux · Windows 8.1 or higher
Python version: Python 3.8, 3.9, 3.10, 3.11, and 3.12 (only 64-bit)
Package managers: pip · conda (via conda-forge)
pip
Using pip, sktime releases are available as source packages and binary wheels. Available wheels are listed here.

pip install sktime
or, with maximum dependencies,

pip install sktime[all_extras]
For curated sets of soft dependencies for specific learning tasks:

pip install sktime[forecasting]  # for selected forecasting dependencies
pip install sktime[forecasting,transformations]  # forecasters and transformers
or similar. Valid sets are:

forecasting
transformations
classification
regression
clustering
param_est
networks
annotation
alignment
Cave: in general, not all soft dependencies for a learning task are installed, only a curated selection.

conda
You can also install sktime from conda via the conda-forge channel. The feedstock including the build recipe and configuration is maintained in this conda-forge repository.

conda install -c conda-forge sktime
or, with maximum dependencies,

conda install -c conda-forge sktime-all-extras
(as conda does not support dependency sets, flexible choice of soft dependencies is unavailable via conda)

⚡ Quickstart
Forecasting
from sktime.datasets import load_airline
from sktime.forecasting.base import ForecastingHorizon
from sktime.forecasting.theta import ThetaForecaster
from sktime.split import temporal_train_test_split
from sktime.performance_metrics.forecasting import mean_absolute_percentage_error

y = load_airline()
y_train, y_test = temporal_train_test_split(y)
fh = ForecastingHorizon(y_test.index, is_relative=False)
forecaster = ThetaForecaster(sp=12)  # monthly seasonal periodicity
forecaster.fit(y_train)
y_pred = forecaster.predict(fh)
mean_absolute_percentage_error(y_test, y_pred)
>>> 0.08661467738190656
Time Series Classification
from sktime.classification.interval_based import TimeSeriesForestClassifier
from sktime.datasets import load_arrow_head
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

X, y = load_arrow_head()
X_train, X_test, y_train, y_test = train_test_split(X, y)
classifier = TimeSeriesForestClassifier()
classifier.fit(X_train, y_train)
y_pred = classifier.predict(X_test)
accuracy_score(y_test, y_pred)
>>> 0.8679245283018868
👋 How to get involved
There are many ways to join the sktime community. We follow the all-contributors specification: all kinds of contributions are welcome - not just code.

Documentation	
💝 Contribute	How to contribute to sktime.
🎒 Mentoring	New to open source? Apply to our mentoring program!
📅 Meetings	Join our discussions, tutorials, workshops, and sprints!
👩‍🔧 Developer Guides	How to further develop sktime's code base.
🚧 Enhancement Proposals	Design a new feature for sktime.
🏅 Contributors	A list of all contributors.
🙋 Roles	An overview of our core community roles.
💸 Donate	Fund sktime maintenance and development.
🏛️ Governance	How and by whom decisions are made in sktime's community.
🏆 Hall of fame
Thanks to all our community for all your wonderful contributions, PRs, issues, ideas.


💡 Project vision
By the community, for the community -- developed by a friendly and collaborative community.
The right tool for the right task -- helping users to diagnose their learning problem and suitable scientific model types.
Embedded in state-of-art ecosystems and provider of interoperable interfaces -- interoperable with scikit-learn, statsmodels, tsfresh, and other community favorites.
Rich model composition and reduction functionality -- build tuning and feature extraction pipelines, solve forecasting tasks with scikit-learn regressors.
Clean, descriptive specification syntax -- based on modern object-oriented design principles for data science.
Fair model assessment and benchmarking -- build your models, inspect your models, check your models, and avoid pitfalls.
Easily extensible -- easy extension templates to add your own algorithms compatible with sktime's API.
