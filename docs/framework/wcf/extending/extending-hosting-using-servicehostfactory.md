---
title: Rozšíření hostování pomocí třídy ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806205"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Rozšíření hostování pomocí třídy ServiceHostFactory
Standardní <xref:System.ServiceModel.ServiceHost> rozhraní API pro hostování služby Windows Communication Foundation (WCF) je bod rozšiřitelnosti architektury WCF. Uživatelé mohou odvozovat vlastní hostitele z <xref:System.ServiceModel.ServiceHost>, obvykle k přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> používat <xref:System.ServiceModel.Description.ServiceDescription> výchozí koncové body imperativní přidávat nebo upravovat chování před otevřením službu.  
  
 V prostředí hostování na vlastním serveru nemáte vytvoření vlastní <xref:System.ServiceModel.ServiceHost> protože napsat kód, který vytvoří instanci hostitele a pak zavolají <xref:System.ServiceModel.ICommunicationObject.Open> na něm po vytvoření instance ho. Mezi tyto dva kroky můžete provést libovolně. Například může přidat novou <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Tento přístup není opakovaně použitelné. Kód, který zpracovává popis je zakódovaný do hostitelského programu (v tomto případě funkce Main()), takže je obtížné znovu použít tuto logiku v jiném kontextu. Existují také další způsoby přidávání <xref:System.ServiceModel.Description.IServiceBehavior> nevyžadují imperativní kódu. Odvozujete atribut z <xref:System.ServiceModel.ServiceBehaviorAttribute> a umístí, na implementaci služby typu nebo můžete vytvořit vlastní chování konfigurovat a vytvořit dynamicky pomocí konfigurace.  
  
 Ale mírné varianta příkladu lze také chcete tento problém vyřešit. Jeden z přístupů je přesunout kód, který přidá ServiceBehavior mimo `Main()` a do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda vlastní odvozený ze <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 Potom uvnitř z `Main()` můžete použít:  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Nyní máte zapouzdřené vlastní logiky do čistého abstrakce, která lze snadno opětovně použít napříč mnoha spustitelné soubory jiného hostitele.  
  
 Není-li si hned zjevné, jak používat tento vlastní <xref:System.ServiceModel.ServiceHost> z v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS). Těchto prostředích se liší od hostování na vlastním prostředí, protože jeden vytvoření instance hostitelského prostředí <xref:System.ServiceModel.ServiceHost> jménem aplikace. Hostování infrastruktury služby IIS a WAS neví nic o vaše vlastní <xref:System.ServiceModel.ServiceHost> odvozených.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Byl navržen k vyřešení tohoto problému přístup k vaší vlastní <xref:System.ServiceModel.ServiceHost> z v rámci služby IIS nebo WAS. Protože vlastní hostitelů, který je odvozený od <xref:System.ServiceModel.ServiceHost> dynamicky nastavena a potenciálně různých typů hostitelské prostředí nikdy vytvoří z něj přímo. Místo toho WCF využívá vzor objektu pro vytváření zajistit úroveň dereference mezi hostitelské prostředí a konkrétní typ služby. Pokud k tomu nedostane jinak, používá výchozí implementaci třídy <xref:System.ServiceModel.Activation.ServiceHostFactory> která vrací instanci třídy <xref:System.ServiceModel.ServiceHost>. Ale můžete taky zadat vlastní objekt factory, který vrátí odvozené hostiteli tak, že zadáte název vaší implementace objektu factory v typu CLR @ServiceHost – direktiva.  
  
 Účelem je, že pro základní případy implementace vlastní objekt pro vytváření musí být splněny následující cvičení. Zde je vlastní například <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrací odvozeným <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Místo výchozí objekt pro vytváření použít tento objekt pro vytváření, zadejte název typu ve @ServiceHost – direktiva následujícím způsobem:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Když neexistuje žádné technické omezení na to, co chcete <xref:System.ServiceModel.ServiceHost> vrátíte z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste vaší implementace objektu pro vytváření co nejjednodušší. Pokud máte velké množství vlastní logiky, je lepší uvést tuto logiku uvnitř hostitele místo uvnitř objektu pro vytváření, tak, aby bylo možné znovu použitelné.  
  
 Neexistuje jeden další vrstvě pro hostování rozhraní API, které by se měla uvádět v tomto poli. WCF má také <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> odvozena v uvedeném pořadí. Pro pokročilejší scénáře, kde musí vyměnit velké části systém metadat s vlastními přizpůsobené páskách těch, které neexistují.
