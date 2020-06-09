---
title: 'Postupy: Vytvoření služby, která přijímá libovolná data, pomocí programovacího modelu WCF REST'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: d908651f7815c102b45ea106f5bec4c07d869950
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601332"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Postupy: Vytvoření služby, která přijímá libovolná data, pomocí programovacího modelu WCF REST
Vývojáři někdy musí mít plnou kontrolu nad tím, jak se data vracejí z operace služby. Toto je případ, kdy operace služby musí vracet data ve formátu, který není podporován byWCF. Toto téma popisuje použití programovacího modelu WCF REST k vytvoření služby, která přijímá libovolná data.  
  
### <a name="to-implement-the-service-contract"></a>Implementace kontraktu služby  
  
1. Definujte kontrakt služby. Operace, která přijímá libovolná data, musí mít parametr typu <xref:System.IO.Stream> . Kromě toho musí být tento parametr jediným parametrem předaným v těle žádosti. Operace popsaná v tomto příkladu také přebírá parametr filename. Tento parametr se předává v rámci adresy URL požadavku. Můžete určit, že se má parametr předat v rámci adresy URL zadáním <xref:System.UriTemplate> v <xref:System.ServiceModel.Web.WebInvokeAttribute> . V tomto případě identifikátor URI, který se používá k volání této metody, končí na "UploadFile/nějaký-filename". Část {filename} šablony identifikátoru URI určuje, že parametr filename pro operaci je předán v rámci identifikátoru URI, který se používá k volání operace.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Implementujte kontrakt služby. Kontrakt má pouze jednu metodu, `UploadFile` která přijímá soubor libovolných dat v datovém proudu. Operace načte datový proud, který počítá počet přečtených bajtů, a pak zobrazí název souboru a počet přečtených bajtů.  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a>Hostování služby  
  
1. Vytvořte konzolovou aplikaci, která bude hostovat službu.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. Vytvořte proměnnou, která bude uchovávat základní adresu pro službu v rámci `Main` metody.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Vytvořte <xref:System.ServiceModel.ServiceHost> instanci služby, která určuje třídu služby a základní adresu.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. Přidejte koncový bod, který určuje kontrakt, <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otevřete hostitele služby. Služba je nyní připravena přijímat požadavky.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Programové volání služby  
  
1. Vytvoří <xref:System.Net.HttpWebRequest> s identifikátorem URI použitým pro volání služby. V tomto kódu je základní adresa kombinována s `"/UploadFile/Text"` . `"UploadFile"`Část identifikátoru URI určuje operaci, která se má volat. `"Test.txt"`Část identifikátoru URI určuje parametr filename, který bude předána `UploadFile` operaci. Obě tyto položky jsou namapovány na <xref:System.UriTemplate> použití pro kontrakt operace.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. Nastavte <xref:System.Net.HttpWebRequest.Method%2A> vlastnost na <xref:System.Net.HttpWebRequest> `POST` a a <xref:System.Net.HttpWebRequest.ContentType%2A> vlastnost na `"text/plain"` . Tato služba oznamuje službě, že kód odesílá data a že data jsou v prostém textu.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. Zavolejte <xref:System.Net.HttpWebRequest.GetRequestStream%2A> na získat datový proud požadavku, vytvořte data, která chcete odeslat, zapište tato data do datového proudu požadavků a zavřete datový proud.  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4. Získejte odpověď ze služby voláním <xref:System.Net.HttpWebRequest.GetResponse%2A> a zobrazením dat odpovědi do konzoly.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Zavřete hostitele služby.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam kódu pro tento příklad.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Při kompilování referenčního kódu System. ServiceModel. dll a System. ServiceModel. Web. dll  
  
## <a name="see-also"></a>Viz také

- [UriTemplate a UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
- [Přehled programovacího modelu webových služeb HTTP WCF](wcf-web-http-programming-model-overview.md)
