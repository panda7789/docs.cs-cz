---
title: Přehled vytváření koncových bodů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: bf6bfb10123223bf689945ef93ff09219a68092c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319930"
---
# <a name="endpoint-creation-overview"></a>Přehled vytváření koncových bodů

Veškerá komunikace se službou Windows Communication Foundation (WCF) probíhá prostřednictvím *koncových bodů* služby. Koncové body poskytují klientům přístup k funkcím, které služba WCF nabízí. Tato část popisuje strukturu koncového bodu a popisuje, jak definovat koncový bod v konfiguraci a v kódu.

## <a name="the-structure-of-an-endpoint"></a>Struktura koncového bodu

Každý koncový bod obsahuje adresu, která indikuje, kde najít koncový bod, vazbu, která určuje, jak klient může komunikovat s koncovým bodem, a kontrakt, který identifikuje dostupné metody.

- **Adresa**. Adresa jednoznačně identifikuje koncový bod a oznamuje potenciálním příjemcům, kde se služba nachází. Je reprezentovaná v objektovém modelu WCF pomocí <xref:System.ServiceModel.EndpointAddress> adresy, která obsahuje identifikátor URI (Uniform Resource Identifier) a vlastnosti adresy, které obsahují identitu, některé prvky WSDL (Web Services Description Language) a kolekci volitelných hlaviček. Volitelná záhlaví poskytují dodatečné podrobné informace o adresách, které umožňují identifikovat nebo komunikovat s koncovým bodem. Další informace najdete v tématu [určení adresy koncového bodu](specifying-an-endpoint-address.md).

- **Vazba**. Vazba určuje, jak komunikovat s koncovým bodem. Tato vazba určuje, jak koncový bod komunikuje s celým světem, včetně přenosového protokolu, který se má použít (například TCP nebo HTTP), který kódování má být použito pro zprávy (například text nebo binární), a které požadavky na zabezpečení jsou nezbytné (pro Příklad: SSL (Secure Sockets Layer) [SSL] nebo zabezpečení zpráv SOAP). Další informace najdete v tématu [použití vazeb ke konfiguraci služeb a klientů](using-bindings-to-configure-services-and-clients.md).

- **Kontrakt služby**. Kontrakt služby popisuje, jaké funkce koncový bod zpřístupňuje klientovi. Kontrakt Určuje operace, které může klient volat, formu zprávy a typ vstupních parametrů nebo data potřebná k volání operace a druh zprávy o zpracování nebo odpovědi, kterou může klient očekávat. Tři základní typy smluv odpovídají základním vzorům výměny zpráv (MEPs): datagram (jednosměrný), Request/Reply a duplexní přenos (obousměrný). Kontrakt služby může také využívat data a kontrakty zpráv, aby při přistupování vyžadoval konkrétní datové typy a formáty zpráv. Další informace o tom, jak definovat kontrakt služby, najdete v tématu [Navrhování kontraktů služby](designing-service-contracts.md). Upozorňujeme, že klient může být taky nutný k implementaci kontraktu definovaného službou, kterému se říká kontrakt zpětného volání, aby přijímal zprávy ze služby v duplexní MEP. Další informace najdete v tématu [duplexní služby](./feature-details/duplex-services.md).

Koncový bod pro službu lze zadat buď imperativně pomocí kódu, nebo deklarativně prostřednictvím konfigurace. Pokud nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou. Definování koncových bodů v kódu obvykle není praktické, protože vazby a adresy nasazené služby se obvykle liší od těch, které se použily při vývoji služby. Obecně je praktické definovat koncové body služby pomocí konfigurace namísto kódu. Zachování vazby a adresování informací z kódu umožňuje jejich změnu bez nutnosti opětovné kompilace a opětovného nasazení aplikace.

> [!NOTE]
> Při přidávání koncového bodu služby, který provádí zosobnění, je nutné buď použít jednu z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod, nebo metodu <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> pro správné načtení kontraktu do nového objektu <xref:System.ServiceModel.Description.ServiceDescription>.

## <a name="defining-endpoints-in-code"></a>Definování koncových bodů v kódu

Následující příklad ukazuje, jak zadat koncový bod v kódu s následujícím:

- Definujte kontrakt pro `IEcho` typ služby, který přijímá jméno a odpověď uživatele s odpovědí "Hello \<Name >!".

- Implementujte službu `Echo` typu definovaného smlouvou `IEcho`.

- Zadejte adresu koncového bodu `http://localhost:8000/Echo` služby.

- Nakonfigurujte službu `Echo` pomocí <xref:System.ServiceModel.WSHttpBinding> vazby.

```csharp
namespace Echo
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
> Hostitel služby se vytvoří se základní adresou a potom zbytek adresy, která je relativní vzhledem k základní adrese, je zadána jako součást koncového bodu. Tento oddíl adresy umožňuje lépe definovat více koncových bodů pro služby na hostiteli.

> [!NOTE]
> Vlastnosti <xref:System.ServiceModel.Description.ServiceDescription> v aplikaci služby se nesmí upravovat za metodou <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ServiceHostBase>. Někteří členové, jako je například vlastnost <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> a `AddServiceEndpoint` metody v <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.ServiceHost>, vyvolávají výjimku, pokud byla změněna za daný bod. Jiné vám umožní je upravovat, ale výsledek není definován.
>
> Podobně na straně klienta nesmí být hodnoty <xref:System.ServiceModel.Description.ServiceEndpoint> po volání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>upravovat. Vlastnost <xref:System.ServiceModel.ChannelFactory.Credentials%2A> vyvolá výjimku, pokud byla změněna za chvíli. Ostatní hodnoty popisů klienta lze upravovat bez chyb, ale výsledek není definován.
>
> Bez ohledu na to, jestli pro službu nebo klienta, se doporučuje změnit popis před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="defining-endpoints-in-configuration"></a>Definování koncových bodů v konfiguraci

Při vytváření aplikace často chcete odložit rozhodnutí správci, který aplikaci nasazuje. Například neexistuje žádný způsob, jak si předem zjistit, co bude adresa služby (identifikátor URI). Místo hardwarového zakódování adresy je vhodnější dát správcům po vytvoření služby. Tato flexibilita je zajištěna prostřednictvím konfigurace. Podrobnosti najdete v tématu [Konfigurace služeb](configuring-services.md).

> [!NOTE]
> K rychlému vytvoření konfiguračních souborů použijte nástroj pro tvorbu [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) s *názvem `/config:`filename*`[,`*filename*`]` přepínač.

## <a name="using-default-endpoints"></a>Používání výchozích koncových bodů

Pokud v kódu nebo v konfiguraci nejsou zadány žádné koncové body, modul runtime poskytuje výchozí koncové body přidáním jednoho výchozího koncového bodu pro každou základní adresu pro každý kontrakt služby implementovaný službou. Základní adresu lze zadat v kódu nebo v konfiguraci a výchozí koncové body jsou přidány při volání <xref:System.ServiceModel.ICommunicationObject.Open> v <xref:System.ServiceModel.ServiceHost>. Tento příklad je stejný jako v předchozí části, ale vzhledem k tomu, že nejsou zadány žádné koncové body, jsou přidány výchozí koncové body.

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
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

 Pokud jsou zadány koncové body explicitně, lze výchozí koncové body přidat voláním <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> před voláním <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Další informace o výchozích koncových bodech najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Viz také:

- [Implementace kontraktů služeb](implementing-service-contracts.md)
