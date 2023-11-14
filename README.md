# raftlib

Step 1: Update the ubuntu system packages

sudo apt-get update && sudo apt-get upgrade

Step 2: Install required tools and packages

sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

HelloWorld.cpp
#include <raft>
#include <raftio>
#include <cstdlib>
#include <string>

class HelloWorld : public raft::kernel
{
public:
    HelloWorld() : raft::kernel()
    {
        //Thêm port, khai báo tên, kiểu dữ liệu của port 
        output.addPort<std::string>("0");
    }

    virtual raft::kstatus run()
    {
        //Chỉ in ra một dòng chữ "Hello World"
        output["0"].push(std::string("Hello World\n"));

        //Gửi tín hiệu dừng
        return (raft::stop);
    }
};

int main(int argc, char **argv)
{
    //Đầu ra là console 
    raft::print<std::string> p;

    //Tạo đối tượng lớp Hello 
    HelloWorld hello;
    
    //Tạo đối tượng map 
    raft::map m;
    
    //Thêm các đối tượng vào map theo đúng thứ tự 
    m += hello >> p;
    
    //Thực thi map 
    m.exe();

    //Dừng chương trình 
    return (EXIT_SUCCESS);
}
