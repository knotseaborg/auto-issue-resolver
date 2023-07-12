# Beyond Bootstrapping: Automatic resolution of issues in large-scale GitHub repositories.
GPT-4 has been proven to be effective at bootstrapping software projects, but can it be used to maintain complex, large-scale projects? This project is an attempt at creating a tool capable of such a feat.

## How it (should) works!
![image](https://github.com/knotseaborg/auto-issue-resolver/assets/24828420/d191212d-e089-4353-aa50-4d6b35b2355b)

The goal is to leverage GPT-4 to generate code by understanding the issue raised, and the discussion between participants. Although the issues can be expressed in a free format, most large-scale projects have pre-define templates including detailed description, fix suggestions, minimally reproduceable code etc., which should greatly help in generating a solution. 

## Notable features
1. Use of code graph to traverse relevant reference code
2. Automatic creation of test-cases and deployment of test-environment.
3. Self evaluation of generated solution
4. The solution is iteratively improved by considering possible variations when taking new reference code into account.

## A closer look at the setup
1. Code-graph generation
    * Rudimentary forms of code-graphs already exist, through which GitHub & plugins in editors too reference definitions of objects to statically perform syntax validation and provide suggestions. With further work, this can possibly be extended to create a code-graph.
2. Setting up multiple test environments for parallel resolution of different issues.
    * When an issue is raised, it is either for a feature request or bug resolution. For either cases, a suitable test environment can be automatically created inside a container by extracting necessary parameters from the issue description.

<div align="center">
  <img src="https://github.com/knotseaborg/auto-issue-resolver/assets/24828420/b0c728d4-be10-420e-a597-d27d2603a675" width="800"/>
</div>

## A closer look at generating the solution
In addition to the reference code, the model will be iteratively exposed to new blocks of code in a sliding window-like process. This way the model can propose multiple solutions, out of which the best solution can be proposed. 
To make the process more efficient, further restrictions can be applied to filter the new blocks of code based on relevancy through documentation and signatures.
<br>
![image](https://github.com/knotseaborg/auto-issue-resolver/assets/24828420/3f283c2c-bb81-471e-b160-201011258305)
