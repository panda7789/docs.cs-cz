---
title: Rozšíření hostování pomocí třídy ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: de6a590b94285872dd77006eda7f86d5d629be9d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849900"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Rozšíření hostování pomocí třídy ServiceHostFactory
Standardní <xref:System.ServiceModel.ServiceHost> rozhraní API pro hostování služeb v Windows Communication Foundation (WCF) je bod rozšíření v architektuře WCF. Uživatelé mohou odvodit své vlastní třídy hostitelů <xref:System.ServiceModel.ServiceHost>z, obvykle přepsat <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> pro použití <xref:System.ServiceModel.Description.ServiceDescription> pro přidání výchozích koncových bodů imperativně nebo změnit chování před otevřením služby.  
  
 V prostředí pro vlastní hostování nemusíte vytvářet vlastní <xref:System.ServiceModel.ServiceHost> , protože píšete kód, který vytváří instance hostitele, a pak ho zavolat <xref:System.ServiceModel.ICommunicationObject.Open> po jeho vytvoření. Mezi těmito dvěma kroky můžete provádět cokoli, co potřebujete. Můžete například přidat nové <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Tento přístup nejde opakovaně použít. Kód, který pracuje s popisem, je kódován do hostitelského programu (v tomto případě funkce main ()), takže je obtížné znovu použít tuto logiku v jiných kontextech. Existují také další způsoby přidávání <xref:System.ServiceModel.Description.IServiceBehavior> , které nevyžadují imperativní kód. Můžete odvodit atribut z <xref:System.ServiceModel.ServiceBehaviorAttribute> a umístit ho do typu implementace služby, nebo můžete vytvořit vlastní chování a vytvořit ho dynamicky pomocí konfigurace.  
  
 K vyřešení tohoto problému ale můžete použít i mírnou variaci tohoto příkladu. Jedním z přístupů je přesunutí kódu, který přidá ServiceBehavior z `Main()` a <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> do metody vlastního odvozeného <xref:System.ServiceModel.ServiceHost>:  
  
```csharp
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
  
 Pak můžete v `Main()` nástroji použít:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Nyní jste zapouzdři vlastní logiky do čisté abstrakce, kterou je možné snadno znovu použít v mnoha různých spustitelných souborech hostitele.  
  
 Ihned není zřejmé, jak používat tuto vlastní <xref:System.ServiceModel.ServiceHost> verzi v rámci služby Internetová informační služba (IIS) nebo aktivační služby procesů systému Windows (WAS). Tato prostředí se liší od prostředí pro samostatné hostování, protože hostující prostředí je jedním z instancí <xref:System.ServiceModel.ServiceHost> aplikace. Infrastruktura služby IIS a byla hostingová infrastruktura neznala žádné informace <xref:System.ServiceModel.ServiceHost> o vašem vlastním derivátu.  
  
 Byl navržen pro řešení tohoto problému s přístupem k vlastnímu <xref:System.ServiceModel.ServiceHost> z IIS nebo was. <xref:System.ServiceModel.Activation.ServiceHostFactory> Vzhledem k tomu, že vlastní hostitel, <xref:System.ServiceModel.ServiceHost> který je odvozen z aplikace, je dynamicky nakonfigurován a potenciálně různých typů, hostující prostředí jej nikdy nevytváří instance přímo. Místo toho WCF používá model továrny k zajištění vrstvy dereference mezi hostujícím prostředím a konkrétním typem služby. Pokud to neuděláte jinak, používá výchozí implementaci <xref:System.ServiceModel.Activation.ServiceHostFactory> , která vrací <xref:System.ServiceModel.ServiceHost>instanci. Můžete ale také zadat vlastní továrnu, která vrátí vašeho odvozeného hostitele zadáním názvu typu CLR implementace výroby v @ServiceHost direktivě.  
  
 Záměrem je, že implementace vlastního továrny by měla být přímým výkonem. Například zde je vlastní <xref:System.ServiceModel.Activation.ServiceHostFactory> , který vrací odvozenou: <xref:System.ServiceModel.ServiceHost>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Chcete-li použít tuto továrnu namísto výchozího objektu pro vytváření, zadejte název typu @ServiceHost v direktivě následujícím způsobem:  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 I když nebudete mít k <xref:System.ServiceModel.ServiceHost> dispozici žádný technický limit k tomu, abyste se mohli vrátit z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, doporučujeme, abyste zajistili, že vaše tovární implementace bude co nejjednodušší. Pokud máte spoustu vlastní logiky, je lepší tuto logiku umístit do svého hostitele místo do továrny, aby ji bylo možné znovu použít.  
  
 Rozhraní API pro hostování obsahuje jednu vrstvu, která by zde měla být zmíněná. WCF má <xref:System.ServiceModel.ServiceHostBase> také a <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, ze kterého <xref:System.ServiceModel.ServiceHost> a <xref:System.ServiceModel.Activation.ServiceHostFactory> v tomto případě jsou odvozeny. Ty existují pro pokročilejší scénáře, kdy je nutné odpínat velké části systému metadat vlastními přizpůsobenými vytvářeními.
