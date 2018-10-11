---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: b72c3959b2a42c6a5abc8ef31975d5bdb9ce220e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086840"
---
# <a name="endpoint-creation-overview"></a>Přehled vytváření koncových bodů
Veškerá komunikace se službou Windows Communication Foundation (WCF) nastane prostřednictvím *koncové body* služby. Koncové body poskytují klientům přístup k funkci, která nabízí služby WCF. Tato část popisuje strukturu koncový bod a ukazuje, jak definovat koncový bod v konfiguraci a v kódu.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura koncový bod  
 Každý koncový bod obsahuje adresu, která označuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem a kontrakt, který identifikuje dostupné metody.  
  
-   **Adresa**. Adresa jednoznačně identifikuje koncový bod a říká potenciálním zákazníkům, kde se služba nachází. Je zastoupena v objektový model WCF pomocí <xref:System.ServiceModel.EndpointAddress> adresu, která obsahuje identifikátor URI (Uniform Resource) a vlastnosti adresy, které zahrnují identitu, některé prvky webové služby WSDL (Description Language) a kolekce volitelné záhlaví. Volitelná záhlaví poskytují další podrobné informace o adresování k identifikaci a k interakci s koncovým bodem. Další informace najdete v tématu [zadání adresy koncového bodu](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Vytvoření vazby**. Vazba Určuje, jak se ke komunikaci s koncovým bodem. Určuje vazbu, jak koncový bod komunikuje s ostatními, včetně protokolu přenosu (například TCP nebo HTTP), kódování, které pro zprávy (například text nebo binary) a jaké požadavky na zabezpečení, které jsou nezbytné (pro například Secure Sockets Layer [SSL] nebo zabezpečení zprávy protokolu SOAP). Další informace najdete v tématu [pomocí vazby na konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Kontrakt služby**. Kontrakt služby popisuje, jaké funkce zpřístupňuje koncový bod do klienta. Kontrakt určuje operace, které můžete volat klienta, formulář zprávy a typ vstupních parametrů nebo data potřebná pro volání operace a druh zpracování nebo zprávy s odpovědí, kterou můžete očekávat, že klient. Tři základní typy kontraktů odpovídají základní zprávy exchange vzory (MEPs): datagram (jednocestné), požadavek/odpověď a přenos (obousměrné). Kontrakt služby můžete použít taky data a zprávy smlouvy tak, aby vyžadovala konkrétní datové typy a formáty zpráv při, ke kterému přistupujete. Další informace o tom, jak definování kontraktu služby najdete v tématu [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md). Všimněte si, že klient může rovněž vyžaduje, aby implementace kontraktu služby definované, volá se, kontrakt zpětného volání pro příjem zpráv ze služby v duplexním MEP. Další informace najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Koncový bod služby lze toho pomocí kódu nebo deklarativně prostřednictvím konfigurace. Pokud nejsou zadány žádné koncové body modul runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každou smlouvu službou implementována. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně je praktičtější k definování koncových bodů služby pomocí konfigurace namísto kódu. Udržování vazby a adresování informace mimo kód umožňující změnit bez nutnosti znovu kompilovat a opětovné nasazení aplikace.  
  
> [!NOTE]
>  Při přidávání koncového bodu služby, který provádí zosobnění, je nutné použít jeden z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody nebo <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda správně načíst smlouvy do nové <xref:System.ServiceModel.Description.ServiceDescription> objektu.  
  
## <a name="defining-endpoints-in-code"></a>Definování koncových bodů v kódu  
 Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícími možnostmi:  
  
-   Definují kontrakt `IEcho` typ služby, který přijímá název jiného uživatele a zpětné vazby pomocí odpověď "Hello \<jméno >!".  
  
-   Implementace `Echo` služby typu definované `IEcho` kontraktu.  
  
-   Zadejte adresu koncového bodu z `http://localhost:8000/Echo` pro službu.  
  
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
>  Hostitel služby je vytvořen pomocí základní adresu a pak je zbytek adresy, relativní k základní adresa, zadaný jako součást koncového bodu. Toto rozdělení do oddílů adresy umožňuje více koncových bodů, snadněji pro služby na hostiteli.  
  
> [!NOTE]
>  Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> ve službě application nesmí upravit subsequent tak, aby <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodu na <xref:System.ServiceModel.ServiceHostBase>. Některé členy, jako <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> vlastnost a `AddServiceEndpoint` metody <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolat výjimku, pokud byl změněn za tímto bodem. Ostatní umožňují upravovat, ale výsledek není definován.  
>   
>  Podobně na straně klienta <xref:System.ServiceModel.Description.ServiceEndpoint> hodnoty nesmí být změněny po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Vlastnost vyvolá výjimku, pokud byl změněn za tímto bodem. Ostatní hodnoty Popis klienta můžete změnit bez chyb, ale výsledek není definován.  
>   
>  Ať už pro službu nebo klienta, se doporučuje, že upravíte popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definování koncových bodů v konfiguraci  
 Při vytváření aplikace, často chcete odložit rozhodnutí správce, který je nasazení aplikace. Například je často bude vědět předem, jaké služby Adresa (URI). Místo pevného kódování adresu, je vhodnější umožňují správcům udělat po vytvoření služby. Díky této flexibilitě se provádí prostřednictvím konfigurace. Podrobnosti najdete v tématu [konfigurace služby](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) s `/config:` *filename*`[,`*filename* `]` přepnout na rychle vytvořte konfigurační soubory.  
  
## <a name="using-default-endpoints"></a>Pomocí výchozí koncové body  
 Pokud nejsou zadány žádné koncové body, v kódu nebo v konfiguraci modulu runtime poskytuje výchozí koncové body přidáním jeden výchozí koncový bod pro každou základní adresu pro každou smlouvu službou implementována. Základní adresa se dá nastavit v kódu nebo v konfiguraci a jsou přidány výchozí koncové body, kdy <xref:System.ServiceModel.ICommunicationObject.Open> je volán na <xref:System.ServiceModel.ServiceHost>. Tento příklad je stejný příklad z předchozí části, ale protože nejsou zadány žádné koncové body, jsou přidány výchozí koncové body.  
  
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
  
 Pokud koncové body jsou explicitně zadán, výchozí koncové body může být přidána voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Další informace o výchozí koncové body, naleznete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
