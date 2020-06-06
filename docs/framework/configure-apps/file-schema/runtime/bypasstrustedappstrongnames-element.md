---
title: Element <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739093"
---
# <a name="bypasstrustedappstrongnames-element"></a>Element \<bypassTrustedAppStrongNames>

Určuje, zda se má obejít ověření silných názvů u sestavení s úplným vztahem důvěryhodnosti, která jsou načtena do úplného vztahu důvěryhodnosti <xref:System.AppDomain> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a>Syntaxe

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda je povolena funkce obcházení, která zabraňuje ověřování silných názvů pro sestavení s úplným vztahem důvěryhodnosti. Když je tato funkce povolená, silné názvy se při načtení sestavení neověřují na správnost. Výchozí formát je `true`.|

## <a name="enabled-attribute"></a>Atribut enabled

|Hodnota|Description|
|-----------|-----------------|
|`true`|Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti nejsou ověřovány, pokud jsou sestavení načtena do plně důvěryhodného vztahu důvěryhodnosti <xref:System.AppDomain> . Toto nastavení je výchozí.|
|`false`|Signatury silného názvu v sestaveních s úplným vztahem důvěryhodnosti jsou ověřovány, když jsou sestavení načtena do plně důvěryhodného vztahu důvěryhodnosti <xref:System.AppDomain> . Podpis silného názvu je kontrolován pouze pro správnost signatury; Nejedná se o porovnání s jiným silným názvem pro porovnání.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|

## <a name="remarks"></a>Poznámky

Funkce obcházení silného názvu nezpůsobí režii ověřování podpisů silného názvu u sestavení s úplným vztahem důvěryhodnosti.

Funkce obcházení se vztahuje na jakékoli sestavení, které je podepsáno silným názvem a které má následující vlastnosti:

- Plně důvěryhodné bez <xref:System.Security.Policy.StrongName> legitimace (například má `MyComputer` legitimaci zóny).

- Načteno do plně důvěryhodného <xref:System.AppDomain> .

- Načteno z umístění pod <xref:System.AppDomainSetup.ApplicationBase%2A> vlastností <xref:System.AppDomain> .

- Nepodepsaná se zpožděním.

> [!NOTE]
> Pokud byla funkce obcházení vypnutá pro všechny aplikace v počítači pomocí klíče registru, nemá tento nastavení konfiguračního souboru žádný vliv. Další informace najdete v tématu [Postup: zákaz funkce obcházení silného názvu](../../../../standard/assembly/disable-strong-name-bypass-feature.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak určit chování, které ověřuje signaturu silného názvu u sestavení s úplným vztahem důvěryhodnosti.

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Postupy: zákaz funkce obcházení silného názvu](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
