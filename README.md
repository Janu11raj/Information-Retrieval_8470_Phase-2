# Information-Retrieval_8470_Phase-2
## Course Recommender System needs to Consider the Job Market 
## Introduction
This project implements a personalized course recommendation system that considers job market trends to optimize learner skill development. The system integrates Skill Extraction and Matching (SEM) and reinforcement learning-based recommendations using the Advantage Actor-Critic (A2C) model. Unlike traditional approaches, A2C dynamically updates learner profiles, ensuring optimal course recommendations for long-term employability.
## Installation
Requires Python 3.10 or higher.
## Install Dependencies
pip install -r requirements.txt
## Usage
python "/IR A2C/jcrec/pipeline.py" --config "/IR A2C/config/run.yaml"
## Configuration File (run.yaml)
taxonomy_path: IR A2C/data/taxonomy.csv  # Path to taxonomy file-
course_path: IR A2C/data/courses.json  # Path to courses file-
cv_path: IR A2C/data/resumes.json  # Path to resumes file
job_path: IR A2C/data/jobs.json  # Path to jobs file
mastery_levels_path: IR A2C/data/mastery_levels.json  # Path to mastery levels
results_path: IR A2C/results  # Directory for saving results

level_3: true  # Use only third level of taxonomy (fewer skills)
nb_courses: 100  # Number of courses (-1 to use all)
nb_cvs: -1  # Number of resumes (-1 to use all)
max_cv_skills: 15  # Max skills per resume
nb_jobs: 100  # Number of jobs (-1 to use all)
threshold: 0.8  # Similarity threshold
k: 2  # Number of recommended courses per user

model: a2c  # Model type (greedy, optimal, dqn, ppo, a2c)
total_steps: 5000  # Training steps for reinforcement learning
eval_freq: 500  # Evaluation frequency during training
nb_runs: 1  # Number of experiment runs
seed: 42  # Random seed for reproducibility
## Description of Source Files (src/)
File	Description
pipeline.py	Main script to train and evaluate models.
Greedy.py	Implements greedy recommendation strategy.
Optimal.py	Implements optimal recommendation strategy.
Reinforce.py	Implements reinforcement learning-based recommendations using A2C.
CourseRecEnv.py	Defines custom reinforcement learning environment using gymnasium.
Dataset.py	Loads and processes resumes, courses, and jobs.
matchings.py	Implements matching, similarity, and relevance functions.
## Example Training Output (A2C)
Loaded config from: /home/jrajend/IR A2C/config/run.yaml
Using model: a2c
Dataset with 52 learners, 100 jobs, 100 courses and 46 skills.
Running A2C model for run 1/1...
Iteration 5000. Average jobs: 0.923 Time: 0.193 sec
Average Recommendation Time: 0.0029 sec
New Learner Attractiveness Score: 848.17
New Applicable Jobs Per Learner: 0.96




taxonomy_path: data/taxonomy.csv # Path to the taxonomy file
course_path: data/courses.json # Path to the courses file
cv_path: data/resumes.json # Path to the resumes file
job_path: data/jobs.json # Path to the jobs file
mastery_levels_path: data/mastery_levels.json # Path to the mastery levels file
results_path: results # Path to the results directory where results are saved
level_3: true # Whether to use only the third level of the taxonomy and not the fourth  (if true: less skills)
nb_courses: 100 # Number of courses to use (set to -1 to use all)
nb_cvs: -1 # Number of resumes to use (set to -1 to use all)
max_cv_skills: 15 # Maximum number of skills per resume
nb_jobs: 100 # Number of jobs to use (set to -1 to use all)
threshold: 0.8 # Threshold for the similarities
k: 2 # Number of courses to recommend
model: greedy # Model to use (greedy, optimal, dqn, ppo, a2c)
total_steps: 50000 # Total number of steps for the training of the agent
eval_freq: 5000 # Frequency of the evaluation of the agent
nb_runs: 1 # Number of runs (set to 1 for greedy and optimal since they are deterministic)
seed: 42 # Seed for the random number generator

