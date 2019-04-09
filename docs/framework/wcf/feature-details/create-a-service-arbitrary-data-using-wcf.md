---
title: 'Postupy: Vytvoření služby, která přijímá libovolná data – pomocí programovacího modelu WCF REST'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: c03450c66cf8de14d6c638550a510a91593c45b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144076"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Postupy: Vytvoření služby, která přijímá libovolná data – pomocí programovacího modelu WCF REST
Vývojáři v některých případech musí mít úplnou kontrolu nad jak se data vrácená z operace služby. To je případ, kdy operace služby musí vracet data ve formátu není podporován byWCF. Toto téma popisuje použití programovacího modelu WCF REST k vytvoření služby, která přijímá libovolná data.  
  
### <a name="to-implement-the-service-contract"></a>Implementace kontraktu služby  
  
1.  Definování kontraktu služby. Operace, která přijímá libovolná data musí mít parametr typu <xref:System.IO.Stream>. Kromě toho tento parametr musí být jediným parametrem předané v textu požadavku. Operace popsané v tomto příkladu má také parametr filename. Tento parametr je předáván v rámci URL požadavku. Můžete určit, že je parametr předaný v rámci URL zadáním <xref:System.UriTemplate> v <xref:System.ServiceModel.Web.WebInvokeAttribute>. V tomto případě identifikátor URI se používá k volání této metody končí na "UploadFile/některé-název souboru". Část "{filename}" Šablona identifikátoru URI Určuje, že parametr filename pro tuto operaci je předán v rámci identifikátoru URI používá k volání operace.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  Implementace kontraktu služby. Smlouva obsahuje pouze jednu metodu `UploadFile` , která obdrží soubor libovolná data v datovém proudu. Operace načte datový proud monitorovat počet bajtů čtení a potom zobrazí název souboru a počet přečtených bajtů.  
  
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
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvořte konzolovou aplikaci pro hostování služby.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  Vytvořte proměnnou pro uchování základní adresu pro službu v rámci `Main` metody.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Vytvoření <xref:System.ServiceModel.ServiceHost> instance služby, který určuje třídu služby a základní adresa.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  Přidat koncový bod, který určuje kontrakt, <xref:System.ServiceModel.WebHttpBinding>, a <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Otevření hostitele služby. Služba je nyní připravena přijímat požadavky.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Volat službu prostřednictvím kódu programu  
  
1.  Vytvoření <xref:System.Net.HttpWebRequest> se identifikátor URI použitý k vyvolání služby. V tomto kódu je základní adresa kombinovat s `"/UploadFile/Text"`. `"UploadFile"` Část identifikátoru URI určuje operaci, která volání. `"Test.txt"` Část identifikátoru URI specifikuje název souboru parametr předat `UploadFile` operace. Obě tyto položky namapovat <xref:System.UriTemplate> použitý pro kontrakt.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  Nastavte <xref:System.Net.HttpWebRequest.Method%2A> vlastnost <xref:System.Net.HttpWebRequest> k `POST` a <xref:System.Net.HttpWebRequest.ContentType%2A> vlastnost `"text/plain"`. Služba říká, že kód je odesílání dat a dat je ve formátu prostého textu.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  Volání <xref:System.Net.HttpWebRequest.GetRequestStream%2A> zobrazíte datový proud požadavku vytvořit data odeslat, zapisovat data do datového proudu požadavku a zavřete datový proud.  
  
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
  
4.  Získat odpověď ze služby voláním <xref:System.Net.HttpWebRequest.GetResponse%2A> a zobrazovat data odpovědi do konzoly.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  Zavřete hostitele služby.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis kódu v tomto příkladu.  
  
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
  
-   Při kompilaci kódu – odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll  
  
## <a name="see-also"></a>Viz také:

- [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Přehled modelu webového programování HTTP služby WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
