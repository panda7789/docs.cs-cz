---
title: 'Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 9753fbc9b333cb7e89ddc8dff030cb1f62ede23b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600358"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="75ca7-102">Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="75ca7-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="75ca7-103">Vývojáři někdy musí mít plnou kontrolu nad tím, jak se data vracejí z operace služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="75ca7-104">Toto je případ, kdy operace služby musí vracet data ve formátu, který není podporován službou WCF.</span><span class="sxs-lookup"><span data-stu-id="75ca7-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="75ca7-105">Toto téma popisuje použití programovacího modelu webové služby HTTP WCF k vytvoření takové služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="75ca7-106">Tato služba má jednu operaci, která vrací datový proud.</span><span class="sxs-lookup"><span data-stu-id="75ca7-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="75ca7-107">Implementace kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="75ca7-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="75ca7-108">Definujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-108">Define the service contract.</span></span> <span data-ttu-id="75ca7-109">Kontrakt se nazývá `IImageServer` a má jednu metodu volanou `GetImage` , která vrací <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="75ca7-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="75ca7-110">Vzhledem k tomu, že metoda vrátí <xref:System.IO.Stream> , WCF předpokládá, že operace má úplnou kontrolu nad bajty vracené z operace služby a neplatí pro vrácená data formátování.</span><span class="sxs-lookup"><span data-stu-id="75ca7-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="75ca7-111">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-111">Implement the service contract.</span></span> <span data-ttu-id="75ca7-112">Kontrakt má pouze jednu operaci ( `GetImage` ).</span><span class="sxs-lookup"><span data-stu-id="75ca7-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="75ca7-113">Tato metoda generuje rastrový obrázek a uloží jej do <xref:System.IO.MemoryStream> formátu. jpg.</span><span class="sxs-lookup"><span data-stu-id="75ca7-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="75ca7-114">Tato operace pak tento datový proud vrátí volajícímu.</span><span class="sxs-lookup"><span data-stu-id="75ca7-114">The operation then returns that stream to the caller.</span></span>  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     <span data-ttu-id="75ca7-115">Všimněte si druhého na poslední řádek kódu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="75ca7-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="75ca7-116">Tím se nastaví záhlaví typu obsahu na `"image/jpeg"` .</span><span class="sxs-lookup"><span data-stu-id="75ca7-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="75ca7-117">I když tento příklad ukazuje, jak vrátit soubor. jpg, může být upraven tak, aby vracel libovolný typ dat, který je požadován, v jakémkoli formátu.</span><span class="sxs-lookup"><span data-stu-id="75ca7-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="75ca7-118">Operace musí načíst nebo vygenerovat data a pak ji zapsat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="75ca7-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="75ca7-119">Hostování služby</span><span class="sxs-lookup"><span data-stu-id="75ca7-119">To host the service</span></span>  
  
1. <span data-ttu-id="75ca7-120">Vytvořte konzolovou aplikaci, která bude hostovat službu.</span><span class="sxs-lookup"><span data-stu-id="75ca7-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="75ca7-121">Vytvořte proměnnou, která bude uchovávat základní adresu pro službu v rámci `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="75ca7-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="75ca7-122">Vytvořte <xref:System.ServiceModel.ServiceHost> instanci pro službu, která určuje třídu služby a základní adresu.</span><span class="sxs-lookup"><span data-stu-id="75ca7-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="75ca7-123">Přidejte koncový bod pomocí <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="75ca7-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="75ca7-124">Otevřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="75ca7-125">Počkejte, dokud uživatel nestiskne klávesu ENTER a službu ukončí.</span><span class="sxs-lookup"><span data-stu-id="75ca7-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="75ca7-126">Volání nezpracované služby pomocí aplikace Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="75ca7-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="75ca7-127">Spusťte službu, měli byste vidět následující výstup služby.</span><span class="sxs-lookup"><span data-stu-id="75ca7-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="75ca7-128">Otevřete Internet Explorer a zadejte `http://localhost:8000/Service/GetImage?width=50&height=40` žlutý obdélník s modrou úhlopříčnou čárou přes střed.</span><span class="sxs-lookup"><span data-stu-id="75ca7-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75ca7-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="75ca7-129">Example</span></span>  
 <span data-ttu-id="75ca7-130">Následuje úplný seznam kódu pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="75ca7-130">The following is a complete listing of the code for this topic.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75ca7-131">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="75ca7-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="75ca7-132">Při kompilování ukázkového referenčního kódu System. ServiceModel. dll a System. ServiceModel. Web. dll.</span><span class="sxs-lookup"><span data-stu-id="75ca7-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ca7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="75ca7-133">See also</span></span>

- [<span data-ttu-id="75ca7-134">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="75ca7-134">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
