---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cd6f937811ae503dd4de7ff989510c4eb8b8933
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252449"
---
# <a name="netfx40_legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy> Element

Určuje, zda modul runtime používá starší zásady zabezpečení přístupu kódu (CAS).

[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_LegacySecurityPolicy >**  

## <a name="syntax"></a>Syntaxe

```xml
<NetFx40_LegacySecurityPolicy
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

Následující části popisují atributy, podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá starší zásady CAS.|

## <a name="enabled-attribute"></a>Atribut enabled

|Value|Popis|
|-----------|-----------------|
|`false`|Modul runtime nepoužívá starší zásady CAS. Toto nastavení je výchozí.|
|`true`|Modul runtime používá starší zásady CAS.|

### <a name="child-elements"></a>Podřízené elementy

Žádné

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Popis|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|

## <a name="remarks"></a>Poznámky

V .NET Framework verze 3,5 a starších verzích je zásada CAS vždy platná. V .NET Framework 4 musí být povolená zásada CAS.

Zásada CAS je specifická pro verzi. Vlastní zásady CAS, které existují v dřívějších verzích .NET Framework, je nutné přezadat v .NET Framework 4.

Použití elementu na sestavení .NET Framework 4 nemá vliv na [Kód transparentní z zabezpečení](../../../misc/security-transparent-code.md); pravidla transparentnosti jsou stále používána. `<NetFx40_LegacySecurityPolicy>`

> [!IMPORTANT]
> Použití prvku může mít za následek výrazné snížení výkonu pro sestavení nativních imagí vytvořená [generátorem nativních bitových kopií (Ngen. exe)](../../../tools/ngen-exe-native-image-generator.md) , které nejsou nainstalované v [globální mezipaměti sestavení (GAC](../../../app-domains/gac.md)). `<NetFx40_LegacySecurityPolicy>` Snížení výkonu je způsobeno neschopností modulu runtime načíst sestavení jako nativní bitové kopie, pokud je atribut použit, což vede k tomu, že jsou načítána jako sestavení za běhu.

> [!NOTE]
> Zadáte-li cílovou verzi .NET Framework, která je starší než .NET Framework 4 v nastavení projektu pro projekt aplikace Visual Studio, bude zásada CAS povolena, včetně všech vlastních zásad CAS, které jste zadali pro danou verzi. Nebudete však moci použít nové typy a členy .NET Framework 4. Můžete také zadat dřívější verzi .NET Framework pomocí [ \<prvku > supportedRuntime](../startup/supportedruntime-element.md) ve schématu nastavení spouštění v [konfiguračním souboru aplikace](../../index.md).

> [!NOTE]
> Syntaxe konfiguračního souboru rozlišuje velká a malá písmena. Měli byste použít syntaxi, jak je uvedeno v části syntaxe a příklady.

## <a name="configuration-file"></a>Konfigurační soubor

Tento element lze použít pouze v konfiguračním souboru aplikace.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak u aplikace povolit starší zásady CAS.

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
