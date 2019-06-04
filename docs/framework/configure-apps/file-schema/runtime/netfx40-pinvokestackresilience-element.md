---
title: Element <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7a1cf34f63b1ba0dfced8ff23c252f3363723c6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489406"
---
# <a name="netfx40pinvokestackresilience-element"></a>\<Netfx40_pinvokestackresilience – > – Element
Určuje, zda modul runtime automaticky opravy nesprávné volání nespravovaného kódu deklarace v době běhu, za cenu pomalejší přechody mezi spravováno a nespravovaný kód.  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime zjistí nesprávné platformu vyvolání deklarace a automaticky opravuje zásobníku za běhu na 32bitových platformách.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`0`|Modul runtime používá rychlejší zprostředkovatele komunikace s objekty zařazování architektura zavedena v rozhraní .NET Framework 4, které není možné zjistit a opravte nesprávné volání nespravovaného kódu deklarace. Toto nastavení je výchozí.|  
|`1`|Modul runtime používá pomalejší přechody zjistit a opravit nesprávný platformu vyvolání deklarace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek umožňuje obchodu rychlejší zařazování spolupráce pro za běhu odolnost proti nesprávné platformu vyvolání deklarace.  
  
 Od verze rozhraní .NET Framework 4, poskytuje efektivnější spolupráce zařazování architektura významné výkonnostní zlepšení pro přechody ze spravovaného kódu do nespravovaného kódu. V dřívějších verzích rozhraní .NET Framework zařazování vrstvy zjistil nesprávný platformu vyvolání deklarace na 32bitových platformách a automaticky opravit, zásobníku. Nová architektura zařazování eliminuje tento krok. V důsledku toho přechody jsou velmi rychlé zpracování, ale nesprávné nespravovaného kódu deklarace může způsobit selhání programu.  
  
 Chcete-li snadno zjistit nesprávná deklarace během vývoje, jsme vylepšili ladění prostředí sady Visual Studio. [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) pomocníka spravovaného ladění (MDA) upozorní nesprávné platformy vyvoláte deklarace když vaše aplikace běží s připojeným ladícím nástrojem.  
  
 K řešení scénářů, kde vaše aplikace používá komponenty, nelze znovu zkompilovat a, že máte nesprávné vyvolání platformy deklarace, můžete použít `NetFx40_PInvokeStackResilience` elementu. Přidání tohoto prvku do konfiguračního souboru aplikace s `enabled="1"` požádá o do režimu kompatibility s chováním dřívějších verzích rozhraní .NET Framework za cenu pomalejší přechodů. Sestavení, která byla zkompilována proti dřívějších verzích rozhraní .NET Framework, vyloučí se automaticky do tohoto režimu kompatibility a není nutné tento element.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob, jakým do zvýšení odolnosti proti nesprávné vyvolání platformy deklarace pro aplikaci za cenu pomalejší přechody mezi spravovaného a nespravovaného kódu.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
