---
title: 'C# vyhrazené atributy: Podmíněné, Zastaralé, AttributeUsage'
ms.date: 04/09/2020
description: Tyto atributy jsou interpretovány kompilátorem ovlivnit kód generovaný kompilátorem
ms.openlocfilehash: c6d697dd08233ffc88900949998047137ee170a9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021763"
---
# <a name="reserved-attributes-conditionalattribute-obsoleteattribute-attributeusageattribute"></a>Vyhrazené atributy: ConditionalAttribute, ObsoleteAttribute, AttributeUsageAttribute

Tyto atributy lze použít na prvky v kódu. Přidávají těmto prvkům sémantický význam. Kompilátor používá tyto sémantické významy změnit svůj výstup a sestavy možných chyb vývojáři pomocí kódu.

## <a name="conditional-attribute"></a>Atribut `Conditional`

Atribut `Conditional` umožňuje provádění metody závislé na identifikátor předběžného zpracování. Atribut `Conditional` je alias <xref:System.Diagnostics.ConditionalAttribute>pro aplikaci a lze jej použít na metodu nebo třídu atributu.

V následujícím příkladu `Conditional` se používá metoda povolení nebo zakázání zobrazení diagnostických informací specifických pro program:

:::code language="csharp" source="snippets/trace.cs" interactive="try-dotnet" :::

Pokud `TRACE_ON` identifikátor není definován, výstup trasování se nezobrazí. Prozkoumejte sami v interaktivním okně.

Atribut `Conditional` se často používá `DEBUG` s identifikátorem povolit trasování a protokolování funkce pro ladění sestavení, ale ne ve verzi sestavení, jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditional" :::

Pokud je volána metoda označená jako podmíněná, přítomnost nebo nepřítomnost zadaného symbolu předběžného zpracování určuje, zda je volání zahrnuto nebo vynecháno. Pokud je definován symbol, je zahrnuto volání; v opačném případě je volání vynecháno. Podmíněná metoda musí být metoda v deklaraci třídy `void` nebo struktury a musí mít návratový typ. Použití `Conditional` je čistší, elegantnější a méně náchylné k `#if…#endif` chybám než ohraničování metod uvnitř bloků.

Pokud má metoda `Conditional` více atributů, je zahrnuto volání metody, pokud je definován jeden nebo více podmíněných symbolů (symboly jsou logicky propojeny pomocí operátoru OR). V následujícím příkladu přítomnost `A` buď `B` nebo má za následek volání metody:

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetMultipleConditions" :::

### <a name="using-conditional-with-attribute-classes"></a>Použití `Conditional` s třídami atributů

Atribut `Conditional` lze také použít na definici třídy atributu. V následujícím příkladu bude `Documentation` vlastní atribut přidávat informace `DEBUG` pouze do metadat, pokud je definován.

:::code language="csharp" source="snippets/ConditionalExamples.cs" id="SnippetConditionalConditionalAttribute" :::

## <a name="obsolete-attribute"></a>Atribut `Obsolete`

Atribut `Obsolete` označí prvek kódu jako již doporučený pro použití. Použití entity označené jako zastaralé generuje upozornění nebo chybu. Atribut `Obsolete` je atribut na jedno použití a lze jej použít pro libovolnou entitu, která umožňuje atributy. `Obsolete`je alias <xref:System.ObsoleteAttribute>pro aplikaci .

V následujícím příkladu `Obsolete` je atribut `A` použit `B.OldMethod`pro třídu a metodu . Vzhledem k tomu, že druhý `B.OldMethod` argument `true`konstruktoru atributu aplikovaný na je `A` nastavena na , tato metoda způsobí chybu kompilátoru, vzhledem k tomu, že pomocí třídy pouze vytvoří upozornění. Volání `B.NewMethod`, však nevytváří žádné upozornění nebo chybu. Například při použití s předchozími definicemi, následující kód generuje dvě upozornění a jednu chybu:

:::code language="csharp" source="snippets/ObsoleteExample.cs" interactive="try-dotnet" :::

Řetězec zadaný jako první argument konstruktoru atributu se zobrazí jako součást upozornění nebo chyby. Jsou generována `A` dvě upozornění pro třídu: jeden pro deklaraci odkazu třídy a jeden pro konstruktor třídy. Atribut `Obsolete` lze použít bez argumentů, ale včetně vysvětlení, co použít místo toho se doporučuje.

## <a name="attributeusage-attribute"></a>Atribut `AttributeUsage`

Atribut `AttributeUsage` určuje, jak lze použít vlastní třídu atributu. <xref:System.AttributeUsageAttribute>je atribut, který aplikujete na vlastní definice atributů. Atribut `AttributeUsage` umožňuje řídit:

- U kterých programových prvků může být atribut použit. Pokud neomezíte jeho použití, může být atribut použit na některý z následujících prvků programu:
  - sestavení
  - module
  - pole
  - event
  - method
  - Param
  - property
  - return
  - type
- Určuje, zda lze atribut použít na jeden prvek programu vícekrát.
- Určuje, zda jsou atributy zděděny odvozenými třídami.

Výchozí nastavení vypadá jako v následujícím příkladu při explicitním použití:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageFirst" :::

V tomto příkladu lze třídu `NewAttribute` použít na libovolný podporovaný prvek programu. Ale to může být použita pouze jednou pro každou entitu. Atribut je zděděn odvozenými třídami při použití na základní třídu.

A <xref:System.AttributeUsageAttribute.AllowMultiple> <xref:System.AttributeUsageAttribute.Inherited> argumenty jsou volitelné, takže následující kód má stejný účinek:

:::code language="csharp" source="snippets/NewAttribute.cs" id="SnippetUsageSecond" :::

První <xref:System.AttributeUsageAttribute> argument musí být jeden nebo <xref:System.AttributeTargets> více prvků výčtu. Více typů cílů lze propojit společně s operátorem OR, jako je následující příklad:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetDefinePropertyAttribute" :::

Počínaje C# 7.3, atributy lze použít buď vlastnost nebo záložní pole pro automaticky implementované vlastnosti. Atribut se vztahuje na vlastnost, pokud `field` nezadáte specifikátor atributu. Obě jsou uvedeny v následujícím příkladu:

:::code language="csharp" source="snippets/NewPropertyOrFieldAttribute.cs" id="SnippetUsePropertyAttribute" :::

Pokud <xref:System.AttributeUsageAttribute.AllowMultiple> je `true`argument , pak výsledný atribut lze použít více než jednou na jednu entitu, jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="snippets/MultiUseAttribute.cs" id="SnippetMultiUse" :::

V tomto `MultiUseAttribute` případě lze použít `AllowMultiple` opakovaně, `true`protože je nastavena na . Oba formáty zobrazené pro použití více atributů jsou platné.

Pokud <xref:System.AttributeUsageAttribute.Inherited> `false`je , pak atribut není zděděn podle tříd odvozených z atributu třídy. Příklad:

:::code language="csharp" source="snippets/NonInheritedAttribute.cs" id="SnippetNonInherited" :::

V tomto `NonInheritedAttribute` případě se `DClass` nevztahuje na prostřednictvím dědičnosti.

## <a name="see-also"></a>Viz také

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Atributy](../../../standard/attributes/index.md)
- [Reflexe](../../programming-guide/concepts/reflection.md)
