---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448682"
---
# \<behaviorExtensions>
Rozšíření chování umožňují uživateli vytvářet uživatelsky definované prvky chování. Tyto prvky lze použít společně se standardními prvky chování Windows Communication Foundation (WCF). `behaviorExtensions`Oddíl definuje prvek tak, aby jej bylo možné použít v konfiguraci. Tady je příklad typického rozšíření chování.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Chcete-li přidat možnosti konfigurace elementu, je nutné zapsat a zaregistrovat prvek konfigurace. Další informace najdete v <xref:System.Configuration> dokumentaci.  
  
 Po definování prvku a jeho typu konfigurace lze použít rozšíření, jak je znázorněno v následujícím příkladu.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Zabezpečení  
 Důrazně doporučujeme použít plně kvalifikované názvy sestavení při registraci typů v `machine.config` `app.config` souborech a. Pokud typ není definován jednoznačně, vyhledá zavaděč typu CLR v následujících umístěních v zadaném pořadí:  
  
 Pokud je známo sestavení typu, zavaděč vyhledá umístění pro přesměrování konfiguračního souboru, GAC, aktuální sestavení s použitím informací o konfiguraci a základního adresáře aplikace. Pokud je sestavení neznámé, zavaděč vyhledá aktuální sestavení, mscorlib a umístění vrácené `TypeResolve` obslužnou rutinou události. Toto pořadí vyhledávání CLR lze upravit pomocí háčků, jako je mechanismus předávání typů a událost AppDomain. TypeResolve.  
  
 Útočník může zneužít pořadí vyhledávání CLR a spustit neautorizovaný kód. Použití plně kvalifikovaných (silných) názvů jednoznačně identifikuje typ a zvyšuje zabezpečení systému.  
  
 Další informace najdete v tématu [jak modul runtime vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md) a <xref:System.AppDomain.TypeResolve> .  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Konfigurace a rozšíření modulu runtime s chováním](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
