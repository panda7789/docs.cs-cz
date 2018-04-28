---
title: Přehled vytváření koncových bodů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f7e12f3a6c5d722b2eda1eaaeb390ee3284a70e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="endpoint-creation-overview"></a>Přehled vytváření koncových bodů
Veškerá komunikace s [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby dojde k prostřednictvím *koncové body* služby. Koncové body poskytují klientům přístup k funkcím, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nabídky služeb. Tato část popisuje strukturu koncový bod a popisuje, jak definovat koncový bod v konfiguraci a v kódu.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura koncový bod  
 Každý koncový bod obsahuje adresu, která určuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem a kontrakt, který identifikuje dostupné metody.  
  
-   **Adresa**. Adresa jednoznačně identifikuje koncový bod a potenciální spotřebitelé informuje, kde se služba nachází. Je zobrazena v [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] objektový model pomocí <xref:System.ServiceModel.EndpointAddress> adresu, která obsahuje identifikátor URI (Uniform Resource) a vlastnosti adresy, které zahrnují identity, některé prvky webové služby popis Language (WSDL) a kolekce volitelné hlavičky. Volitelné hlavičky poskytují další podrobné adresování informace k identifikaci nebo interakci s koncovým bodem. Další informace najdete v tématu [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Vazba**. Vazba Určuje, jak ke komunikaci s koncovým bodem. Vazba Určuje, jak koncový bod komunikuje s na světě, včetně které přenosový protokol použít (například TCP nebo HTTP), které kódování určené k použití pro zprávy (například textu nebo binárních) a jsou nezbytné (pro které požadavky na zabezpečení například Secure Sockets Layer [SSL] nebo zabezpečení protokolu SOAP zprávy). Další informace najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Kontrakt služby**. Kontrakt služby popisuje, jaké funkce koncový bod vystavuje klienta. Kontrakt určuje operace, které můžete volat klienta, formulář zprávy a typ vstupní parametry nebo data potřebná k volání operace a typ zpracování nebo zprávu odpovědi, které můžete očekávat klienta. Tři základní typy kontraktů odpovídají základní zpráva exchange vzory (MEPs): datagram (jednocestné), požadavek nebo odpověď a duplexní režim (obousměrné). Kontrakt služby můžete také použít kontraktů dat a zpráv tak, aby vyžadovala konkrétní datové typy a formáty zpráv, pokud přistupuje. [!INCLUDE[crabout](../../../includes/crabout-md.md)] definování kontraktu služby najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md). Všimněte si, že klient může rovněž vyžaduje, aby implementace kontraktu služby definované, názvem kontraktu zpětného volání pro příjem zpráv z služby v rámci duplexní MEP. Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Koncový bod pro službu lze imperativní pomocí kódu nebo deklarativně pomocí konfigurace. Pokud nejsou zadány žádné koncové body modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu. Definování koncové body v kódu obvykle není praktické protože jsou obvykle liší od těch, které používá při služby je vyvíjen vazeb a adresy pro v nasazené službě. Obecně je praktičtější definovat koncové body služby pomocí konfigurace, nikoli kódu. Zachování vazby a adresování informace mimo kód vám umožní se změnit bez nutnosti znovu zkompiluje a znovu nasaďte aplikaci.  
  
> [!NOTE]
>  Při přidávání koncový bod služby, který provádí zosobnění, je nutné použít jeden z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody nebo <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda správně načíst smlouvy do nové <xref:System.ServiceModel.Description.ServiceDescription> objektu.  
  
## <a name="defining-endpoints-in-code"></a>Definování koncové body v kódu  
 Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícími službami:  
  
-   Definování kontraktu pro `IEcho` typ služby, který přijímá název jiného uživatele a zpětné vazby pomocí odpověď "Hello \<name >!".  
  
-   Implementace `Echo` služby typu definované `IEcho` kontrakt.  
  
-   Zadejte adresu koncového bodu z http://localhost:8000/Echo pro službu.  
  
-   Konfigurace `Echo` služby pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  Hostitel služby se vytvoří základní adresu a potom je zbytek adresy, relativně k základní adresu, zadaný jako součást koncový bod. Toto rozdělení do oddílů adresy umožňuje víc koncových bodů být snadněji definované pro služby na hostiteli.  
  
> [!NOTE]
>  Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě aplikace nesmí být upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu <xref:System.ServiceModel.ServiceHostBase>. Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody na <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, způsobí výjimku, pokud se změní za tento bod. Ostatní umožňují je upravovat, ale výsledek není definován.  
>   
>  Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> po zavolání nesmí měnit hodnoty <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud se změní za tento bod. Ostatní hodnoty klienta popis můžete změnit bez chyby, ale výsledek není definován.  
>   
>  Zda se služba nebo klienta, se doporučuje, když je upravit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definování koncové body v konfiguraci  
 Při vytváření aplikace, budete chtít často odložení rozhodnutí týkající se na správce, který je nasazení aplikace. Například je často bude žádný způsob, jak zjistit předem jaké služby adres (URI). Místo pevně kódováno adresu, je vhodnější umožňují správcům udělat po vytvoření služby. Tato možnost se provádí prostřednictvím konfigurace. Podrobnosti najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config:` *filename*`[,`*filename* `]` přepnout na rychle vytvořte konfigurační soubory.  
  
## <a name="using-default-endpoints"></a>Pomocí výchozí koncové body  
 Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každý kontrakt služby implementované službu. Základní adresa může být určený v kódu nebo v konfiguraci a jsou výchozí koncové body se přidají při <xref:System.ServiceModel.ICommunicationObject.Open> se volá na <xref:System.ServiceModel.ServiceHost>. V tomto příkladu je příkladě z předchozí části, ale vzhledem k tomu, že nejsou zadány žádné koncové body, se přidají jsou výchozí koncové body.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 Pokud jsou k dispozici explicitně koncových bodů, jsou výchozí koncové body může být přidán voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)] výchozí koncové body, najdete v části [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
