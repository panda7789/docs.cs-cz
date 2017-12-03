---
title: '&lt;behaviorExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c520a8a06a593d8937ca840602ba5bcc7b2d44b4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Chování rozšíření zajistit, aby uživatel k vytváření prvků uživatelem definované chování. Tyto prvky můžete použít spolu s standardní elementy chování Windows Communication Foundation (WCF). `behaviorExtensions` Oddíl definuje element tak, že můžete použít v konfiguraci. Tady je příklad typické chování rozšíření.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Přidat konfiguraci dalo k elementu, musíte k zápisu a zaregistrujte konfigurační prvek. Další informace najdete v tématu <xref:System.Configuration> dokumentaci.  
  
 Po elementu a jeho typ konfigurace jsou definovány, rozšíření můžete použít, jak je znázorněno v následujícím příkladu.  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a>Zabezpečení  
 Důrazně doporučujeme použít při registraci typy v sestavení plně kvalifikované názvy `machine.config` a `app.config` soubory. Pokud typ není definováno jednoznačně, vyhledá se zavaděč typ CLR pro něj v následujících umístěních v uvedeném pořadí:  
  
 Pokud je znám sestavení typu zavaděč prohledá umístění konfiguračního souboru přesměrování, GAC, aktuální sestavení pomocí informace o konfiguraci a základní adresář aplikace. Pokud sestavení neznámý, vyhledá zavaděč aktuální sestavení, mscorlib a umístění vrácený `TypeResolve` obslužné rutiny události. Toto pořadí hledání CLR může upravit s háky například mechanismus předávání typu a AppDomain.TypeResolve události.  
  
 Útočník může zneužít pořadí hledání CLR a spustit neoprávněný kód. Pomocí plně kvalifikované názvy (silné) jednoznačně identifikuje typu a ještě zvyšuje zabezpečení vašeho systému.  
  
 Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](http://go.microsoft.com/fwlink/?LinkId=95336) a <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Konfigurace a rozšíření modulu Runtime s chováním](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
