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
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF
Vývojáři někdy musí mít plnou kontrolu nad tím, jak se data vracejí z operace služby. Toto je případ, kdy operace služby musí vracet data ve formátu, který není podporován službou WCF. Toto téma popisuje použití programovacího modelu webové služby HTTP WCF k vytvoření takové služby. Tato služba má jednu operaci, která vrací datový proud.  
  
### <a name="to-implement-the-service-contract"></a>Implementace kontraktu služby  
  
1. Definujte kontrakt služby. Kontrakt se nazývá `IImageServer` a má jednu metodu volanou `GetImage` , která vrací <xref:System.IO.Stream> .  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Vzhledem k tomu, že metoda vrátí <xref:System.IO.Stream> , WCF předpokládá, že operace má úplnou kontrolu nad bajty vracené z operace služby a neplatí pro vrácená data formátování.  
  
2. Implementujte kontrakt služby. Kontrakt má pouze jednu operaci ( `GetImage` ). Tato metoda generuje rastrový obrázek a uloží jej do <xref:System.IO.MemoryStream> formátu. jpg. Tato operace pak tento datový proud vrátí volajícímu.  
  
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
  
     Všimněte si druhého na poslední řádek kódu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Tím se nastaví záhlaví typu obsahu na `"image/jpeg"` . I když tento příklad ukazuje, jak vrátit soubor. jpg, může být upraven tak, aby vracel libovolný typ dat, který je požadován, v jakémkoli formátu. Operace musí načíst nebo vygenerovat data a pak ji zapsat do datového proudu.  
  
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
  
3. Vytvořte <xref:System.ServiceModel.ServiceHost> instanci pro službu, která určuje třídu služby a základní adresu.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Přidejte koncový bod pomocí <xref:System.ServiceModel.WebHttpBinding> a <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otevřete hostitele služby.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Počkejte, dokud uživatel nestiskne klávesu ENTER a službu ukončí.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Volání nezpracované služby pomocí aplikace Internet Explorer  
  
1. Spusťte službu, měli byste vidět následující výstup služby. `Service is running Press ENTER to close the host`  
  
2. Otevřete Internet Explorer a zadejte `http://localhost:8000/Service/GetImage?width=50&height=40` žlutý obdélník s modrou úhlopříčnou čárou přes střed.  
  
## <a name="example"></a>Příklad  
 Následuje úplný seznam kódu pro toto téma.  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Při kompilování ukázkového referenčního kódu System. ServiceModel. dll a System. ServiceModel. Web. dll.  
  
## <a name="see-also"></a>Viz také

- [Programovací model webových služeb HTTP WCF](wcf-web-http-programming-model.md)
