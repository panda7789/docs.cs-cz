---
title: Rozšíření hostování pomocí třídy ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991312"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Rozšíření hostování pomocí třídy ServiceHostFactory
Standardní <xref:System.ServiceModel.ServiceHost> bod rozšiřitelnosti architektury WCF je rozhraní API pro hostování služby Windows Communication Foundation (WCF). Uživatelé můžou odvozovat vlastní hostitele z <xref:System.ServiceModel.ServiceHost>, obvykle k přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> používat <xref:System.ServiceModel.Description.ServiceDescription> výchozí koncové body imperativně přidávat nebo upravovat chování před otevřením služby.  
  
 V prostředí hostování na vlastním serveru, není nutné vytvořit vlastní <xref:System.ServiceModel.ServiceHost> vzhledem k tomu, že napíšete kód, který vytvoří instanci hostitele a poté zavolejte <xref:System.ServiceModel.ICommunicationObject.Open> na něm po vytvořit její instanci. Mezi tyto dva kroky vám pomůžou cokoliv, co chcete. Například můžete přidat nový <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Tento přístup není opakovaně použitelné. Kód, který provádí úpravy popisu je zakódovaný do hostitelského programu (v tomto případě funkce Main()), takže je obtížné znovu použít tuto logiku v jiném kontextu. Existují také jiné způsoby přidání <xref:System.ServiceModel.Description.IServiceBehavior> , které nevyžadují imperativního kódu. Lze odvodit z atributu <xref:System.ServiceModel.ServiceBehaviorAttribute> a vložit, že pro vaše implementace služby typu nebo je můžete konfigurovatelné vlastní chování a tvoří ji dynamicky pomocí konfigurace.  
  
 Však drobnou změnu v příkladu můžete také použít pro vyřešení tohoto problému. Jedním z přístupů je přesunout kód, který přidá ServiceBehavior z celkového počtu `Main()` a do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda vlastní odvozený ze <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Potom ovládacího `Main()` můžete použít:  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Nyní máte zapouzdřené vlastní logiku do čistého abstrakce, která lze snadno opětovně použít napříč mnoha spustitelné soubory jiného hostitele.  
  
 Není-li si hned zjevné, jak používat tento vlastní <xref:System.ServiceModel.ServiceHost> z v rámci Internetové informační služby (IIS) nebo Windows Process Activation Service (WAS). Těchto prostředích se liší od prostředí hostování na vlastním serveru, protože hostitelské prostředí je jeden vytvoření instance <xref:System.ServiceModel.ServiceHost> jménem aplikace. Infrastruktury hostování IIS a WAS neví nic o vaší vlastní <xref:System.ServiceModel.ServiceHost> odvozených děl na základě.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Je navržená pro vyřešení tohoto problému, přístup k vaší vlastní <xref:System.ServiceModel.ServiceHost> z v rámci služby IIS nebo WAS. Protože vlastního hostitele, který je odvozen z <xref:System.ServiceModel.ServiceHost> dynamicky nakonfigurovaný a potenciálně různých typů, hostitelské prostředí nikdy vytvoří z něj přímo. Místo toho WCF používá vzor factory zajistit určitou úroveň dereference mezi hostitelské prostředí a konkrétní typ služby. Pokud dáte ho jinak, používá výchozí implementaci třídy <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací instanci <xref:System.ServiceModel.ServiceHost>. Ale můžete taky zadat vlastní objekt pro vytváření, který vrací odvozené hostitele tak, že zadáte název typu CLR továrny implementace v @ServiceHost směrnice.  
  
 Cílem je, že pro základní případy implementace vlastní objekt pro vytváření by měl přímo dopředné cvičení. Například tady je vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací odvozený <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Pokud chcete použít tento objekt pro vytváření místo výchozí objekt pro vytváření, zadejte název typu v @ServiceHost směrnice následujícím způsobem:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Na to, co byste chtěli se neplatí žádné technická omezení <xref:System.ServiceModel.ServiceHost> vrátit z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste vaše implementace factory co nejjednodušší. Pokud máte velké množství vlastní logiku, je lepší umístěte tuto logiku uvnitř hostitele místo objekt pro vytváření tak, aby ji bylo možné opakovaně použitelné.  
  
 Existuje jeden další vrstvy do hostujícího rozhraní API, která by měla být uvedeny zde. WCF má také <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> odvodit v uvedeném pořadí. Neexistují pro pokročilejší scénáře, ve kterém musí vyměnit velké části metadat systému s vlastní přizpůsobené vytváření.
