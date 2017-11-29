---
title: "&lt;supportPortability –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b46d12ecebae17b7cfe2168b6313be45ad5b04d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability –&gt; – Element
Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementace rozhraní .NET Framework zakázáním výchozí chování, která zpracovává sestavení jako ekvivalentní pro účely přenositelnost aplikace.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<assemblybinding – > elementu  
\<supportPortability – > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|PKT|Požadovaný atribut.<br /><br /> Určuje token veřejného klíče ovlivněných sestavení jako řetězec.|  
|povoleno|Nepovinný atribut.<br /><br /> Určuje, zda se má povolit podpora přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Povolení podpory pro přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework. Toto nastavení je výchozí.|  
|false|Zakažte podporu pro přenositelnost mezi implementace zadané sestavení rozhraní .NET Framework. To umožňuje aplikaci odkazují na více implementace zadaném sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
|`assemblyBinding`|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], podpora je k dispozici automaticky pro aplikace, které můžete použít buď dva implementace rozhraní .NET Framework, například buď implementace rozhraní .NET Framework nebo .NET Framework pro Silverlight implementaci. Dva implementace konkrétní sestavení rozhraní .NET Framework se zobrazují jako ekvivalentní podle vazač sestavení. Tato funkce přenositelnost aplikace v několik scénářů, způsobuje problémy. V těchto případech `<supportPortability>` prvek můžete použít funkci zakážete.  
  
 Jeden z těchto důvodů je sestavení, který má odkazovat implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci sestavení. Návrhář XAML napsané v systému Windows Presentation Foundation (WPF) možná muset odkazovat oba WPF plochy implementaci, pro uživatelské rozhraní nástroje designer a do něj podmnožinu WPF, který je součástí implementace Silverlight. Ve výchozím nastavení odkazy na samostatné způsobit chybu kompilátoru, protože sestavení – vazby vidí dvě sestavení jako ekvivalentní. Tento element zakáže výchozí chování a umožňuje kompilace proběhla úspěšně.  
  
> [!IMPORTANT]
>  Aby kompilátoru k předání informací pro modul common language runtime vazby sestavení logiky, je nutné použít `/appconfig` – možnost kompilátoru k určení umístění souboru app.config, který obsahuje tento element.  
  
## <a name="example"></a>Příklad  
 Následující příklad povolí aplikaci tak, aby měl odkazy na implementace rozhraní .NET Framework a rozhraní .NET Framework pro Silverlight implementaci žádné sestavení rozhraní .NET Framework, který již existuje v obou implementace. `/appconfig` – Možnost kompilátoru použije k určení umístění tohoto souboru app.config.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [/ appconfig (možnosti kompilátoru C#)](http://msdn.microsoft.com/library/ee523958.aspx)  
 [Přehled sjednocení sestavení rozhraní .NET framework](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
