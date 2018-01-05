---
title: "&lt;Netfx40_pinvokestackresilience –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b17816ee6134dc6b3074256093c0cba07419baf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;Netfx40_pinvokestackresilience –&gt; – Element
Určuje, zda modul runtime automaticky opravy vyvolání nesprávný platformy deklarace v době běhu za cenu pomalejší přechodů mezi spravováno a nespravovaného kódu.  
  
 \<Konfigurace >  
\<modul runtime >  
< netfx40_pinvokestackresilience – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime zjistí nesprávné platformy vyvolání deklarace a automaticky opravuje zásobníku v době běhu na 32bitové platformy.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`0`|Modul runtime používá rychlejší zprostředkovatel komunikace s objekty zařazování architektura počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], který nerozpozná a vyvolání platformy nesprávný oprava deklarace. Toto nastavení je výchozí.|  
|`1`|Přechody pomalejší runtime používá, které zjistit a opravit nesprávné platformy vyvolání deklarace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element umožňuje rychlejší zařazování spolupráce pro spuštění odolnost proti nesprávný platformy vyvolání deklarace obchodu.  
  
 Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], poskytuje zjednodušenou interoperabilita zařazování architektura zlepšení výkonu pro přechody ze spravovaného kódu na nespravovaný kód. V dřívějších verzích rozhraní .NET Framework zařazování vrstvy zjistila Nesprávná platforma vyvolání deklarace na platformách 32bitová verze a automaticky napravení zásobníku. Nové architektury zařazování eliminuje tento krok. V důsledku toho jsou velmi rychlé přechody, ale nesprávný platformy vyvolání deklarace může způsobit selhání programu.  
  
 Chcete-li snadno rozpoznat nesprávné prohlášení během vývoje, bylo vylepšeno ladění prostředí sady Visual Studio. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Pomocník spravovaného ladění (MDA) upozorní nesprávný platformy vyvolání deklarace když aplikace běží s ladicím programem připojen.  
  
 Adresa scénářů, kde vaše aplikace používá komponenty nelze znovu zkompiluje, a že jste nesprávný vyvolání platformy deklarace, můžete použít `NetFx40_PInvokeStackResilience` elementu. Přidání tohoto prvku do konfiguračního souboru aplikace s `enabled="1"` požádá do režimu kompatibility s chováním starší verze rozhraní .NET Framework za cenu přechody pomalejší. Sestavení, které sestavili jsme pro starší verze rozhraní .NET Framework se automaticky vyjádřit výslovný souhlas do tohoto režimu kompatibility a není nutné tento element.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element může použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob, který se přidá do Zvýšená odolnost proti nesprávný vyvolání platformy deklarace pro aplikaci za cenu pomalejší přechodů mezi spravovaných a nespravovaných kódu.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
