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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9541c46d029aa9f4e27a459ffcb9f32a7718039b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="6b346-102">Postupy: vytvoření služby, je možné zadat libovolný dat pomocí programovací Model REST WCF</span><span class="sxs-lookup"><span data-stu-id="6b346-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="6b346-103">Vývojáři někdy musí mít plnou kontrolu nad vrácených dat z operace služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="6b346-104">To je případ, kdy operace služby musí vrátit data ve formátu, které nepodporují[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b346-104">This is the case when a service operation must return data in a format not supported by[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="6b346-105">Toto téma popisuje použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací Model REST vytvoření služby, který obdrží libovolná data.</span><span class="sxs-lookup"><span data-stu-id="6b346-105">This topic discusses using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="6b346-106">K implementaci kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="6b346-106">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="6b346-107">Definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-107">Define the service contract.</span></span> <span data-ttu-id="6b346-108">Operace, která přijímá libovolná data musí mít parametr typu <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="6b346-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="6b346-109">Kromě toho tento parametr musí být jediný parametr předaný v textu požadavku.</span><span class="sxs-lookup"><span data-stu-id="6b346-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="6b346-110">Operace popsaná v tomto příkladu také přebírá parametr filename.</span><span class="sxs-lookup"><span data-stu-id="6b346-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="6b346-111">Tento parametr se předává v rámci adresy URL požadavku.</span><span class="sxs-lookup"><span data-stu-id="6b346-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="6b346-112">Můžete určit, že je parametr předaný v rámci adresy URL zadáním <xref:System.UriTemplate> v <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6b346-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="6b346-113">V tomto případě identifikátoru URI používá k volání této metody končí na "UploadFile nebo některá – název souboru".</span><span class="sxs-lookup"><span data-stu-id="6b346-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="6b346-114">Část "{filename}" šablony URI Určuje, že je v rámci identifikátoru URI používá k volání operace předán parametr filename pro operaci.</span><span class="sxs-lookup"><span data-stu-id="6b346-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  <span data-ttu-id="6b346-115">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-115">Implement the service contract.</span></span> <span data-ttu-id="6b346-116">Smlouva obsahuje pouze jednu metodu `UploadFile` , obdrží soubor libovolná data v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="6b346-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="6b346-117">Operaci přečte datový proud počítání počet bajtů, čtení a potom zobrazí název souboru a počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="6b346-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="6b346-118">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="6b346-118">To host the service</span></span>  
  
1.  <span data-ttu-id="6b346-119">Vytvořte konzolovou aplikaci k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="6b346-120">Vytvořte proměnnou pro uložení základní adresa služby v rámci `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="6b346-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="6b346-121">Vytvoření <xref:System.ServiceModel.ServiceHost> instance služby, který určuje třída služby a základní adresu.</span><span class="sxs-lookup"><span data-stu-id="6b346-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="6b346-122">Přidat koncový bod, který určuje kontrakt, <xref:System.ServiceModel.WebHttpBinding>, a <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6b346-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="6b346-123">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-123">Open the service host.</span></span> <span data-ttu-id="6b346-124">Služba je nyní připravena přijímat požadavky.</span><span class="sxs-lookup"><span data-stu-id="6b346-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="6b346-125">Pro volání služby prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6b346-125">To call the service programmatically</span></span>  
  
1.  <span data-ttu-id="6b346-126">Vytvoření <xref:System.Net.HttpWebRequest> se používá k volání služby identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="6b346-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="6b346-127">V tomto kódu je základní adresa kombinovat s `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="6b346-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="6b346-128">`"UploadFile"` Část identifikátoru URI určuje operaci volat.</span><span class="sxs-lookup"><span data-stu-id="6b346-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="6b346-129">`"Test.txt"` Část identifikátoru URI určuje parametr filename předat `UploadFile` operaci.</span><span class="sxs-lookup"><span data-stu-id="6b346-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="6b346-130">Obě tyto položky namapovány na <xref:System.UriTemplate> u operace kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6b346-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  <span data-ttu-id="6b346-131">Nastavte <xref:System.Net.HttpWebRequest.Method%2A> vlastnost <xref:System.Net.HttpWebRequest> k `POST` a <xref:System.Net.HttpWebRequest.ContentType%2A> vlastnost `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="6b346-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="6b346-132">Tato hodnota informuje službu zda kód je odesílání dat a dat je ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="6b346-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  <span data-ttu-id="6b346-133">Volání <xref:System.Net.HttpWebRequest.GetRequestStream%2A> datový proud požadavku získáte vytvořit data k odeslání, zápisu dat do datového proudu požadavku a zavřete datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6b346-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4.  <span data-ttu-id="6b346-134">Získat odpověď ze služby voláním <xref:System.Net.HttpWebRequest.GetResponse%2A> a zobrazení data odpovědi ke konzole.</span><span class="sxs-lookup"><span data-stu-id="6b346-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  <span data-ttu-id="6b346-135">Zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6b346-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="6b346-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b346-136">Example</span></span>  
 <span data-ttu-id="6b346-137">Níže je úplný seznam všech kód v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b346-137">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b346-138">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6b346-138">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6b346-139">Při kompilování kódu – odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll</span><span class="sxs-lookup"><span data-stu-id="6b346-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b346-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b346-140">See Also</span></span>  
 [<span data-ttu-id="6b346-141">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="6b346-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="6b346-142">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="6b346-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="6b346-143">Přehled modelu programování WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="6b346-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
