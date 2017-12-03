---
title: "Postupy: vytvoření služby, je možné zadat libovolný dat pomocí programovací Model REST WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7f868f02f309401c60737af8a69434d175eee1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Postupy: vytvoření služby, je možné zadat libovolný dat pomocí programovací Model REST WCF
Vývojáři někdy musí mít plnou kontrolu nad vrácených dat z operace služby. To je případ, kdy operace služby musí vrátit data ve formátu, které nepodporují[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Toto téma popisuje použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací Model REST vytvoření služby, který obdrží libovolná data.  
  
### <a name="to-implement-the-service-contract"></a>K implementaci kontraktu služby  
  
1.  Definování kontraktu služby. Operace, která přijímá libovolná data musí mít parametr typu <xref:System.IO.Stream>. Kromě toho tento parametr musí být jediný parametr předaný v textu požadavku. Operace popsaná v tomto příkladu také přebírá parametr filename. Tento parametr se předává v rámci adresy URL požadavku. Můžete určit, že je parametr předaný v rámci adresy URL zadáním <xref:System.UriTemplate> v <xref:System.ServiceModel.Web.WebInvokeAttribute>. V tomto případě identifikátoru URI používá k volání této metody končí na "UploadFile nebo některá – název souboru". Část "{filename}" šablony URI Určuje, že je v rámci identifikátoru URI používá k volání operace předán parametr filename pro operaci.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  Implementujte kontrakt služby. Smlouva obsahuje pouze jednu metodu `UploadFile` , obdrží soubor libovolná data v datovém proudu. Operaci přečte datový proud počítání počet bajtů, čtení a potom zobrazí název souboru a počet přečtených bajtů.  
  
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
  
1.  Vytvořte konzolovou aplikaci k hostování služby.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  Vytvořte proměnnou pro uložení základní adresa služby v rámci `Main` metoda.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Vytvoření <xref:System.ServiceModel.ServiceHost> instance služby, který určuje třída služby a základní adresu.  
  
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
  
### <a name="to-call-the-service-programmatically"></a>Pro volání služby prostřednictvím kódu programu  
  
1.  Vytvoření <xref:System.Net.HttpWebRequest> se používá k volání služby identifikátorem URI. V tomto kódu je základní adresa kombinovat s `"/UploadFile/Text"`. `"UploadFile"` Část identifikátoru URI určuje operaci volat. `"Test.txt"` Část identifikátoru URI určuje parametr filename předat `UploadFile` operaci. Obě tyto položky namapovány na <xref:System.UriTemplate> u operace kontrakt.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  Nastavte <xref:System.Net.HttpWebRequest.Method%2A> vlastnost <xref:System.Net.HttpWebRequest> k `POST` a <xref:System.Net.HttpWebRequest.ContentType%2A> vlastnost `"text/plain"`. Tato hodnota informuje službu zda kód je odesílání dat a dat je ve formátu prostého textu.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  Volání <xref:System.Net.HttpWebRequest.GetRequestStream%2A> datový proud požadavku získáte vytvořit data k odeslání, zápisu dat do datového proudu požadavku a zavřete datového proudu.  
  
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
  
4.  Získat odpověď ze služby voláním <xref:System.Net.HttpWebRequest.GetResponse%2A> a zobrazení data odpovědi ke konzole.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  Zavřete hostitele služby.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Příklad  
 Níže je úplný seznam všech kód v tomto příkladu.  
  
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
  
-   Při kompilování kódu – odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll  
  
## <a name="see-also"></a>Viz také  
 [UriTemplate a UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Přehled modelu programování WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
