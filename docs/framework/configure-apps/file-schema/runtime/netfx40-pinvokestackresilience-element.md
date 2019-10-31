---
title: Element <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116164"
---
# <a name="netfx40_pinvokestackresilience-element"></a>\<element > NetFx40_PInvokeStackResilience

Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_PInvokeStackResilience >**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime detekuje nesprávné deklarace vyvolání platformy a automaticky opraví zásobník v době běhu na 32 64bitových platformách.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Popis|
|-----------|-----------------|
|`0`|Modul runtime používá rychlejší interop marshaling architekturu představenou v .NET Framework 4, která nedetekuje a neopravují nesprávné deklarace vyvolání platformy. Toto nastavení je výchozí.|
|`1`|Běhový modul používá pomalejší přechody, které zjišťují a opravují nesprávné deklarace vyvolání platformy.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

Tento prvek umožňuje rychlejší obchodování interop marshaling pro odolnost za běhu proti nesprávným deklaracím vyvolání platformy.

Počínaje .NET Framework 4 nabízí zjednodušená interop marshaling architektura výrazné zlepšení výkonu pro přechody ze spravovaného kódu do nespravovaného kódu. V dřívějších verzích .NET Framework zařazovací vrstva zjistila nesprávnou deklaraci volání platformy na 32ch platformách a automaticky opravila zásobník. Nová architektura zařazování eliminuje tento krok. V důsledku toho jsou přechody velmi rychlé, ale nesprávná deklarace vyvolání platformy může způsobit selhání programu.

Aby bylo možné během vývoje snadno detekovat nesprávné deklarace, Vylepšili jsme prostředí pro ladění sady Visual Studio. Pomocník pro [pInvokeStackImbalance –](../../../debug-trace-profile/pinvokestackimbalance-mda.md) spravované ladění (MDA) vás upozorní na nesprávné deklarace vyvolání platformy, pokud je vaše aplikace spuštěná s připojeným ladicím programem.

Pro řešení scénářů, kde vaše aplikace používá komponenty, které nemůžete znovu kompilovat a které mají nesprávné deklarace vyvolání platformy, lze použít prvek `NetFx40_PInvokeStackResilience`. Přidání tohoto elementu do konfiguračního souboru aplikace pomocí `enabled="1"` výslovný do režimu kompatibility s chováním dřívějších verzí .NET Framework, za cenu pomalejších přechodů. Sestavení, která byla zkompilována v předchozích verzích .NET Framework, jsou automaticky přizpůsobena do tohoto režimu kompatibility a nepotřebují tento prvek.

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít pouze v konfiguračním souboru aplikace.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak se vyjádřit ke zvýšené odolnosti proti nesprávným deklaracím vyvolání platformy pro aplikaci, za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
