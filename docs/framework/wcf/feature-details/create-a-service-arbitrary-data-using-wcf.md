---
title: 'Postupy: Vytvoření služby, která přijímá libovolná data – pomocí programovacího modelu WCF REST'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: d7da3a5c6dd4f04c4d902dab9c2dff40413ddd20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857322"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="6cb92-102">Postupy: Vytvoření služby, která přijímá libovolná data – pomocí programovacího modelu WCF REST</span><span class="sxs-lookup"><span data-stu-id="6cb92-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="6cb92-103">Vývojáři v některých případech musí mít úplnou kontrolu nad jak se data vrácená z operace služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="6cb92-104">To je případ, kdy operace služby musí vracet data ve formátu není podporován byWCF.</span><span class="sxs-lookup"><span data-stu-id="6cb92-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="6cb92-105">Toto téma popisuje použití programovacího modelu WCF REST k vytvoření služby, která přijímá libovolná data.</span><span class="sxs-lookup"><span data-stu-id="6cb92-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="6cb92-106">Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="6cb92-106">To implement the service contract</span></span>  
  
1. <span data-ttu-id="6cb92-107">Definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-107">Define the service contract.</span></span> <span data-ttu-id="6cb92-108">Operace, která přijímá libovolná data musí mít parametr typu <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="6cb92-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="6cb92-109">Kromě toho tento parametr musí být jediným parametrem předané v textu požadavku.</span><span class="sxs-lookup"><span data-stu-id="6cb92-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="6cb92-110">Operace popsané v tomto příkladu má také parametr filename.</span><span class="sxs-lookup"><span data-stu-id="6cb92-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="6cb92-111">Tento parametr je předáván v rámci URL požadavku.</span><span class="sxs-lookup"><span data-stu-id="6cb92-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="6cb92-112">Můžete určit, že je parametr předaný v rámci URL zadáním <xref:System.UriTemplate> v <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6cb92-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="6cb92-113">V tomto případě identifikátor URI se používá k volání této metody končí na "UploadFile/některé-název souboru".</span><span class="sxs-lookup"><span data-stu-id="6cb92-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="6cb92-114">Část "{filename}" Šablona identifikátoru URI Určuje, že parametr filename pro tuto operaci je předán v rámci identifikátoru URI používá k volání operace.</span><span class="sxs-lookup"><span data-stu-id="6cb92-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="6cb92-115">Implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-115">Implement the service contract.</span></span> <span data-ttu-id="6cb92-116">Smlouva obsahuje pouze jednu metodu `UploadFile` , která obdrží soubor libovolná data v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="6cb92-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="6cb92-117">Operace načte datový proud monitorovat počet bajtů čtení a potom zobrazí název souboru a počet přečtených bajtů.</span><span class="sxs-lookup"><span data-stu-id="6cb92-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="6cb92-118">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="6cb92-118">To host the service</span></span>  
  
1. <span data-ttu-id="6cb92-119">Vytvořte konzolovou aplikaci pro hostování služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="6cb92-120">Vytvořte proměnnou pro uchování základní adresu pro službu v rámci `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="6cb92-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="6cb92-121">Vytvoření <xref:System.ServiceModel.ServiceHost> instance služby, který určuje třídu služby a základní adresa.</span><span class="sxs-lookup"><span data-stu-id="6cb92-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="6cb92-122">Přidat koncový bod, který určuje kontrakt, <xref:System.ServiceModel.WebHttpBinding>, a <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6cb92-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="6cb92-123">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-123">Open the service host.</span></span> <span data-ttu-id="6cb92-124">Služba je nyní připravena přijímat požadavky.</span><span class="sxs-lookup"><span data-stu-id="6cb92-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="6cb92-125">Volat službu prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="6cb92-125">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="6cb92-126">Vytvoření <xref:System.Net.HttpWebRequest> se identifikátor URI použitý k vyvolání služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="6cb92-127">V tomto kódu je základní adresa kombinovat s `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="6cb92-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="6cb92-128">`"UploadFile"` Část identifikátoru URI určuje operaci, která volání.</span><span class="sxs-lookup"><span data-stu-id="6cb92-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="6cb92-129">`"Test.txt"` Část identifikátoru URI specifikuje název souboru parametr předat `UploadFile` operace.</span><span class="sxs-lookup"><span data-stu-id="6cb92-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="6cb92-130">Obě tyto položky namapovat <xref:System.UriTemplate> použitý pro kontrakt.</span><span class="sxs-lookup"><span data-stu-id="6cb92-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="6cb92-131">Nastavte <xref:System.Net.HttpWebRequest.Method%2A> vlastnost <xref:System.Net.HttpWebRequest> k `POST` a <xref:System.Net.HttpWebRequest.ContentType%2A> vlastnost `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="6cb92-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="6cb92-132">Služba říká, že kód je odesílání dat a dat je ve formátu prostého textu.</span><span class="sxs-lookup"><span data-stu-id="6cb92-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="6cb92-133">Volání <xref:System.Net.HttpWebRequest.GetRequestStream%2A> zobrazíte datový proud požadavku vytvořit data odeslat, zapisovat data do datového proudu požadavku a zavřete datový proud.</span><span class="sxs-lookup"><span data-stu-id="6cb92-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4. <span data-ttu-id="6cb92-134">Získat odpověď ze služby voláním <xref:System.Net.HttpWebRequest.GetResponse%2A> a zobrazovat data odpovědi do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6cb92-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="6cb92-135">Zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="6cb92-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="6cb92-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="6cb92-136">Example</span></span>  
 <span data-ttu-id="6cb92-137">Následuje úplný výpis kódu v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="6cb92-137">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="6cb92-138">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6cb92-138">Compiling the Code</span></span>  
  
- <span data-ttu-id="6cb92-139">Při kompilaci kódu – odkaz System.ServiceModel.dll a System.ServiceModel.Web.dll</span><span class="sxs-lookup"><span data-stu-id="6cb92-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb92-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cb92-140">See also</span></span>

- [<span data-ttu-id="6cb92-141">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="6cb92-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="6cb92-142">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="6cb92-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="6cb92-143">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="6cb92-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
