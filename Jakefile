var fs = require('fs');
var path = require('path');
var sh = require('execSync');
var exec = require('child_process').exec;
var sys = require('sys')

function puts(error, stdout, stderr) { sys.puts(stdout); if(error)sys.puts(error); }

//Consts

desc('Run Unit Tests');
task('test',function(){
	exec('./node_modules/.bin/mocha --reporter spec',puts);
});

var issuePushPopCommand = function(pushDir,command){
	issueCommand('pushd ' + pushDir + '; ' + command + '; popd;');
}

var ensureExists = function(exists,path){
	if(!exists){
		fs.mkdirSync(path);
	}
}

var issueCommand = function(command){
	
	var result = sh.exec(command.toString());
	console.log(result.stdout);
}

var deleteFolderRecursive = function(path) {
  if( fs.existsSync(path) ) {
    fs.readdirSync(path).forEach(function(file,index){
      var curPath = path + "/" + file;
      if(fs.lstatSync(curPath).isDirectory()) { // recurse
        deleteFolderRecursive(curPath);
      } else { // delete file
        fs.unlinkSync(curPath);
      }
    });
    fs.rmdirSync(path);
  }
};



