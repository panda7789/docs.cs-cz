---
title: 'Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: c85ab6725876a2d523a18c817ce3fd89f0d2285a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184487"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Postupy: Vytvoření služby, která vrací libovolná data pomocí modelu programování webových služeb HTTP WCF
Někdy vývojáři musí mít plnou kontrolu nad tím, jak jsou data vrácena z operace služby. To je případ, kdy operace služby musí vrátit data ve formátu, který není podporován WCF. Toto téma popisuje použití WCF WEB HTTP programovací model k vytvoření takové služby. Tato služba má jednu operaci, která vrací datový proud.  
  
### <a name="to-implement-the-service-contract"></a>K provedení smlouvy o poskytování služeb  
  
1. Definujte servisní smlouvu. Smlouva je `IImageServer` volána a `GetImage` má jednu metodu, která vrací <xref:System.IO.Stream>.  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Vzhledem k <xref:System.IO.Stream>tomu, že metoda vrátí , WCF předpokládá, že operace má úplnou kontrolu nad bajty, které jsou vráceny z operace služby a použije žádné formátování dat, která je vrácena.  
  
2. Implementujte servisní smlouvu. Smlouva má pouze jednu operaci (`GetImage`). Tato metoda generuje bitmapu a pak <xref:System.IO.MemoryStream> ji uložte do formátu .jpg. Operace pak vrátí tento datový proud volajícímu.  
  
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
  
     Všimněte si předposledního řádku kódu:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Tím nastavíte záhlaví `"image/jpeg"`typu obsahu na . Přestože tato ukázka ukazuje, jak vrátit soubor JPG, lze jej upravit tak, aby vrátil libovolný typ dat, který je požadován, v libovolném formátu. Operace musí načíst nebo generovat data a pak je zapsat do datového proudu.  
  
### <a name="to-host-the-service"></a>Chcete-li službu hostit  
  
1. Vytvořte konzolovou aplikaci pro hostování služby.  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. Vytvořte proměnnou pro uložení základní adresy `Main` pro službu v rámci metody.  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Vytvořte <xref:System.ServiceModel.ServiceHost> instanci pro službu určující třídu služby a základní adresu.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Přidejte koncový bod <xref:System.ServiceModel.WebHttpBinding> pomocí <xref:System.ServiceModel.Description.WebHttpBehavior>a .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Otevřete hostitele služby.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Počkejte, až uživatel stiskne klávesu ENTER a ukončí službu.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Volání nezpracované služby pomocí aplikace Internet Explorer  
  
1. Spusťte službu, měli byste vidět následující výstup ze služby. `Service is running Press ENTER to close the host`  
  
2. Otevřete aplikaci `http://localhost:8000/Service/GetImage?width=50&height=40` Internet Explorer a zadejte, měli byste vidět žlutý obdélník s modrou diagonální čárou přes střed.  
  
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
  
- Při kompilaci odkazu na ukázkový kód System.ServiceModel.dll a System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Viz také

- [Programovací model webových služeb HTTP WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
