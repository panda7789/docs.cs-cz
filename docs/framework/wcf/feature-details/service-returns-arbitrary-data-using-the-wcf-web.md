---
title: 'Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 763d62750380f025ae369e1e917b46d4e51874e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498105"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="b5426-102">Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b5426-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="b5426-103">Vývojáři někdy musí mít plnou kontrolu nad vrácených dat z operace služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="b5426-104">To je případ, kdy operace služby musí vrátit data ve formátu, není podporován službou WCF.</span><span class="sxs-lookup"><span data-stu-id="b5426-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="b5426-105">Toto téma popisuje použití WCF WEB HTTP programovací Model k vytvoření těchto služeb.</span><span class="sxs-lookup"><span data-stu-id="b5426-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="b5426-106">Tato služba obsahuje jednu operaci, která vrací datový proud.</span><span class="sxs-lookup"><span data-stu-id="b5426-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="b5426-107">K implementaci kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="b5426-107">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="b5426-108">Definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-108">Define the service contract.</span></span> <span data-ttu-id="b5426-109">Je volána kontrakt `IImageServer` má jednu metodu s názvem `GetImage` , který vrací <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b5426-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="b5426-110">Vzhledem k tomu, že metoda vrátí <xref:System.IO.Stream>, WCF předpokládá, že operace má plnou kontrolu nad bajtů, které jsou vráceny z operace služby, které se použijí bez formátování data, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="b5426-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2.  <span data-ttu-id="b5426-111">Implementujte kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-111">Implement the service contract.</span></span> <span data-ttu-id="b5426-112">Smlouva obsahuje pouze jednu operaci (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="b5426-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="b5426-113">Tato metoda generuje rastrový obrázek a pak ho uložit pro <xref:System.IO.MemoryStream> ve formátu .jpg.</span><span class="sxs-lookup"><span data-stu-id="b5426-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="b5426-114">Operaci poté vrátí tohoto datového proudu volajícímu.</span><span class="sxs-lookup"><span data-stu-id="b5426-114">The operation then returns that stream to the caller.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="b5426-115">Všimněte si, druhý poslední řádek kódu: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="b5426-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="b5426-116">Toto nastaví záhlaví typu obsahu `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="b5426-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="b5426-117">I když tento příklad ukazuje, jak vracet souboru JPG, ho můžete upravit tak, aby vracet libovolný typ dat, která je požadováno, v libovolném formátu.</span><span class="sxs-lookup"><span data-stu-id="b5426-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="b5426-118">Operaci musí načíst nebo budou data generovat a zapisovat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="b5426-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="b5426-119">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="b5426-119">To host the service</span></span>  
  
1.  <span data-ttu-id="b5426-120">Vytvořte konzolovou aplikaci k hostování služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-120">Create a console application to host the service.</span></span>  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="b5426-121">Vytvořte proměnnou pro uložení základní adresa služby v rámci `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="b5426-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="b5426-122">Vytvoření <xref:System.ServiceModel.ServiceHost> instanci pro třídu služby a základní adresa služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="b5426-123">Přidat k koncový bod pomocí <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="b5426-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="b5426-124">Otevření hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-124">Open the service host.</span></span>  
  
    ```  
    host.Open()  
    ```  
  
6.  <span data-ttu-id="b5426-125">Počkejte, dokud uživatel stiskne klávesu ENTER ukončit službu.</span><span class="sxs-lookup"><span data-stu-id="b5426-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="b5426-126">K volání služby nezpracovaná pomocí Internet Exploreru</span><span class="sxs-lookup"><span data-stu-id="b5426-126">To call the raw service using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b5426-127">Spouštění služby, byste měli vidět následující výstup ze služby.</span><span class="sxs-lookup"><span data-stu-id="b5426-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2.  <span data-ttu-id="b5426-128">Otevřete Internet Explorer a zadejte `http://localhost:8000/Service/GetImage?width=50&height=40` byste měli vidět žlutý obdélníku blue diagonálních řádek prostřednictvím centra.</span><span class="sxs-lookup"><span data-stu-id="b5426-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5426-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5426-129">Example</span></span>  
 <span data-ttu-id="b5426-130">Níže je úplný seznam všech kód pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="b5426-130">The following is a complete listing of the code for this topic.</span></span>  
  
```  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5426-131">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b5426-131">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b5426-132">Při kompilování ukázkového kódu odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="b5426-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5426-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5426-133">See Also</span></span>  
 [<span data-ttu-id="b5426-134">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b5426-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
