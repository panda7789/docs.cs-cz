---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: d025497956715913923e839cb6c482f44f96babb
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320701"
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Rozšíření chování povolují uživateli vytvořit uživatelem definované chování elementů. Tyto prvky lze použít společně s standardní prvky chování Windows Communication Foundation (WCF). `behaviorExtensions` Oddíl definuje element tak, že je možné v konfiguraci. Tady je příklad obvyklé chování rozšíření.  
  
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
  
 Chcete-li přidat možnosti konfigurace na prvek, budete muset zápisu a registrace konfiguračního prvku. Další informace najdete v článku <xref:System.Configuration> dokumentaci.  
  
 Po definování elementu a jeho typ konfigurace rozšíření je možné, jak je znázorněno v následujícím příkladu.  
  
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
 Důrazně doporučujeme použít plně kvalifikované názvy sestavení při registraci typů v `machine.config` a `app.config` soubory. Pokud typ není jednoznačně definována, zavaděč modulu CLR typu prohledá v následujících umístěních v uvedeném pořadí:  
  
 Pokud je sestavení typu je známo, prohledá zavaděč konfiguračního souboru přesměrování umístění mezipaměti GAC, aktuální sestavení s využitím informací o konfiguraci a základní adresář aplikace. Pokud sestavení není znám, vyhledá zavaděč aktuální sestavení mscorlib a umístění vrácené `TypeResolve` obslužné rutiny události. Toto pořadí hledání CLR se dají upravovat pomocí háky například mechanismus předávání typu a AppDomain.TypeResolve událostí.  
  
 Útočník může zneužít pořadí hledání modulu CLR a spustit neoprávněný kód. Pomocí plně kvalifikované názvy (silnou) jednoznačně identifikuje typ a ještě zvyšuje zabezpečení vašeho systému.  
  
 Další informace najdete v tématu [jak modul Runtime vyhledává sestavení](https://go.microsoft.com/fwlink/?LinkId=95336) a <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
