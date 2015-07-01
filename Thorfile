class Checklist < Thor
include Thor::Actions

source_root File.dirname(__FILE__)

  desc "execute","This thor script will execute rspec checklist on the targeted server"

  method_option :host, :aliases => "-h", :desc => "target machine hostname/ip"
  method_option :ssh_port, :aliases => "-o", :desc => "target machine ssh port", :default => 22
  method_option :user, :aliases => "-u", :desc => "target machine user"
  method_option :pass, :aliases => "-p", :desc => "target machine password"
  method_option :spass, :aliases => "-s", :desc => "target machine sudo pass"
  method_option :alfglob, :aliases => "-g", :desc => "target machine global properties"
  method_option :alflog, :aliases => "-l", :desc => "target machine alfresco log"
  method_option :alfmmt, :aliases => "-m", :desc => "target machine alfresco_mmt jar"
  method_option :alfwar, :aliases => "-f", :desc => "target machine alfresco war"
  method_option :shrwar, :aliases => "-r", :desc => "target machine share war"

# thor checklist:execute -h 172.29.101.192 -u root -p alfresco -s alfresco -g /opt/alf-installation/tomcat/shared/classes/alfresco-global.properties -l /opt/alf-installation/tomcat/logs/catalina.out -m /opt/alf-installation/bin/alfresco-mmt.jar -f /opt/alf-installation/tomcat/webapps/alfresco.war -r /opt/alf-installation/tomcat/webapps/share.war
# thor checklist:execute -h 127.0.0.1 -o 2222 -u vagrant -p vagrant -s vagrant -g /usr/share/tomcat/shared/classes/alfresco-global.properties -l /usr/share/tomcat-alfresco/logs/alfresco.log -m /usr/share/tomcat/bin/alfresco-mmt.jar -f /usr/share/tomcat-alfresco/webapps/alfresco.war -r /usr/share/tomcat-share/webapps/share.war

  def execute()

       remove_file("test.properties")
       template "props.erb","test.properties"

        puts "Options set:"
        options.each do |key,value|
          puts "#{key}=#{value}"
        end
	      exec "rspec spec"
  end

end
