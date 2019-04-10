---
title: 'Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 55fdc6824ab82bdf3b5913cd600815ed05bd909c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303918"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF
Vývojáři v některých případech musí mít úplnou kontrolu nad jak se data vrácená z operace služby. To je případ, kdy operace služby musí vracet data ve formátu není podporován službou WCF. Toto téma popisuje použití HTTP programovacího modelu WCF WEB k vytvoření takové služby. Tato služba má jednu operaci, která vrací datový proud.  
  
### <a name="to-implement-the-service-contract"></a>Implementace kontraktu služby  
  
1. Definování kontraktu služby. Smlouva se nazývá `IImageServer` a má jednu metodu s názvem `GetImage` , která vrací <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Protože metoda vrátí <xref:System.IO.Stream>WCF se předpokládá, že operace má plnou kontrolu nad bajtů, které jsou vráceny z operace služby a použije se žádné formátování data, která je vrácena.  
  
2. Implementace kontraktu služby. Smlouva obsahuje pouze jednu operaci (`GetImage`). Tato metoda generuje rastrový obrázek a uložte ji <xref:System.IO.MemoryStream> ve formátu .jpg. Operaci poté vrátí volajícímu tohoto datového proudu.  
  
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
  
     Všimněte si, že druhá poslední řádek kódu: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Tím se nastaví záhlaví typu obsahu `"image/jpeg"`. Přestože tento příklad ukazuje, jak vrátit soubor .jpg, může být upraveno vrátit libovolného typu dat, která je požadována v libovolném formátu. Operace nutné získat nebo generování dat a potom se zapsaly do datového proudu.  
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1. Vytvořte konzolovou aplikaci pro hostování služby.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2. Vytvořte proměnnou pro uchování základní adresu pro službu v rámci `Main` metody.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Vytvoření <xref:System.ServiceModel.ServiceHost> instanci pro třídu služby a základní adresa služby.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Přidat koncový bod pomocí <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otevření hostitele služby.  
  
    ```  
    host.Open()  
    ```  
  
6. Počkejte, až uživatel stiskne klávesu ENTER k ukončení služby.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Volat službu nezpracované pomocí aplikace Internet Explorer  
  
1. Spuštění služby, byste měli vidět následující výstup ze služby. `Service is running Press ENTER to close the host`  
  
2. Spusťte aplikaci Internet Explorer a zadejte `http://localhost:8000/Service/GetImage?width=50&height=40` byste měli vidět žlutý obdélníku s modrá čára Úhlopříčný prostřednictvím centra.  
  
## <a name="example"></a>Příklad  
 Následuje úplný výpis kódu pro toto téma.  
  
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
  
-   Při kompilování ukázkového kódu odkazovat na System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také:

- [Model programování webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
