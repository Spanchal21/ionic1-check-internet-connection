# ionic1-check-internet-connection
check internet connection from ionic1 app

required plugin
	
cordova plugin add org.apache.cordova.network-information


     $scope.fnCheckConnection = function(){
       if(window.Connection) { 
            if(navigator.connection.type == Connection.NONE) {

                  $scope.fnAlert();

            }else{
                console.log(navigator.connection.type);
            }
          }else{
                console.log('Cannot find Window.Connection');
          }
     }

    //========= internet conection retry alert ===============
    $scope.fnAlert = function(){
        var myPopup = $ionicPopup.show({
            template: myalert.nointernetconnection,
            scope: $scope,
            buttons: [
                { text: 'OK' }, {
                    text: 'RELOAD',
                    onTap: function(res) {
                        if (res) {
                             $scope.fnCheckConnection();
                        } else {
                            console.log('not sure');
                        }
                    }
                },
            ]
        });
    }
