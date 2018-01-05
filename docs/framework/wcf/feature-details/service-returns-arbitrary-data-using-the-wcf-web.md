---
title: "Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 829e9f2bcf909bee41f53b4b7cabbb0803e77963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF
Vývojáři někdy musí mít plnou kontrolu nad vrácených dat z operace služby. To je případ, kdy operace služby musí vrátit data ve formátu, které nepodporují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Toto téma popisuje použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové HTTP programovací Model pro vytvoření těchto služeb. Tato služba obsahuje jednu operaci, která vrací datový proud.  
  
### <a name="to-implement-the-service-contract"></a>K implementaci kontraktu služby  
  
1.  Definování kontraktu služby. Je volána kontrakt `IImageServer` má jednu metodu s názvem `GetImage` , který vrací <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Vzhledem k tomu, že metoda vrátí <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] předpokládá, že operace má plnou kontrolu nad bajtů, které jsou vráceny z operace služby a se vztahuje na data, která je vrácena žádná formátování.  
  
2.  Implementujte kontrakt služby. Smlouva obsahuje pouze jednu operaci (`GetImage`). Tato metoda generuje rastrový obrázek a pak ho uložit pro <xref:System.IO.MemoryStream> ve formátu .jpg. Operaci poté vrátí tohoto datového proudu volajícímu.  
  
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
  
     Všimněte si, druhý poslední řádek kódu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Toto nastaví záhlaví typu obsahu `"image/jpeg"`. I když tento příklad ukazuje, jak vracet souboru JPG, ho můžete upravit tak, aby vracet libovolný typ dat, která je požadováno, v libovolném formátu. Operaci musí načíst nebo budou data generovat a zapisovat do datového proudu.  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Vytvořte konzolovou aplikaci k hostování služby.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Vytvořte proměnnou pro uložení základní adresa služby v rámci `Main` metoda.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Vytvoření <xref:System.ServiceModel.ServiceHost> instanci pro třídu služby a základní adresa služby.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  Přidat k koncový bod pomocí <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Otevření hostitele služby.  
  
    ```  
    host.Open()  
    ```  
  
6.  Počkejte, dokud uživatel stiskne klávesu ENTER ukončit službu.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>K volání služby nezpracovaná pomocí Internet Exploreru  
  
1.  Spouštění služby, byste měli vidět následující výstup ze služby. `Service is running Press ENTER to close the host`  
  
2.  Otevřete Internet Explorer a zadejte `http://localhost:8000/Service/GetImage?width=50&height=40` byste měli vidět žlutý obdélníku blue diagonálních řádek prostřednictvím centra.  
  
## <a name="example"></a>Příklad  
 Níže je úplný seznam všech kód pro toto téma.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Při kompilování ukázkového kódu odkazovat System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také  
 [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
