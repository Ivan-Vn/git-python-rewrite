#write your own git 
just rewriting git in Python.Why?
1)Is Fun
2) To finally get it 

if fnmatch(path, pattern):
            result = value
    return result #true or false
def check_ignore_scoped(rules, path):
    #Check ignore rules in parent directories
    parent = os.path.dirname(path)
    while True:
        if parent in rules:
            result = check_ignore1(rules[parent], path)
            if result != None:
                return result
        if parent == "":
            break
        parent = os.path.dirname(parent)
    return None
def check_ignore_absolute(rules, path):
    #Check ignore rules in absolute paths
    parent = os.path.dirname(path)
    for ruleset in rules:
        result = check_ignore1(ruleset, path)
        if result != None:
            return result
    return False # This is a reasonable default at this point.
def check_ignore(rules, path):
    #Check if a given path is ignored based on the provided ignore rules
    if os.path.isabs(path):
        raise Exception("This function requires path to be relative to the repository's root")
    result = check_ignore_scoped(rules.scoped, path)
    if result != None:
        return result
    return check_ignore_absolute(rules.absolute, path)
   
          
   




            
