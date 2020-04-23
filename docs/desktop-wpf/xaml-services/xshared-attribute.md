---
title: x:Shared – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: e1cd1d9db5c19decd840b433f986e0ba53557a8b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071372"
---
# <a name="xshared-attribute"></a>x:Shared – atribut

Pokud je `false`nastavena na , upraví wpf chování načítání prostředků tak, aby požadavky na přiřazený prostředek vytvořit novou instanci pro každý požadavek namísto sdílení stejné instance pro všechny požadavky.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<ResourceDictionary>
  <object x:Shared="false".../>
</ResourceDictionary>
```

## <a name="remarks"></a>Poznámky

`x:Shared`je mapován na obor názvů XAML jazyka XAML a je rozpoznán jako platný jazykový prvek XAML službou .NET XAML Services a jejími čtečkami XAML. Uvedené možnosti `x:Shared` jsou však relevantní pouze pro aplikace WPF a pro analyzátor WPF XAML. V WPF, `x:Shared` je užitečné pouze jako atribut, pokud je použita <xref:System.Windows.ResourceDictionary>na objekt, který existuje v rámci WPF . Jiné použití nevyvolání výjimky analýzy nebo jiné chyby, ale nemají žádný vliv.

Význam pro `x:Shared` není specifikován ve specifikaci jazyka XAML. Jiné implementace XAML, například ty, které jsou navazují na služby .NET XAML, nemusí nutně poskytovat podporu pro sdílení prostředků. Takové implementace XAML může poskytnout podobné chování v `x:Shared` podpůrné masy, která také používá hodnoty.

V WPF je `x:Shared` `true`výchozí podmínkou pro prostředky . Tato podmínka znamená, že každý daný požadavek na prostředek vždy vrátí stejnou instanci.

Úprava objektu, který je vrácen prostřednictvím rozhraní API prostředků, <xref:System.Windows.FrameworkElement.FindResource%2A> <xref:System.Windows.ResourceDictionary>například , nebo úpravy objektu přímo v rámci , změní původní prostředek. Pokud odkazy na tento prostředek byly dynamické odkazy na prostředky, spotřebitelé tohoto prostředku získat změněný prostředek.

Pokud odkazy na prostředek byly statické odkazy na prostředky, změny prostředku po [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] zpracování času jsou irelevantní. Další informace o statických a dynamických odkazech na prostředky naleznete v tématu [XAML Resources](../fundamentals/xaml-resources-define.md).

Explicitně `x:Shared="true"` zadání se provádí zřídka, protože to je již výchozí. Neexistuje žádný přímý ekvivalent `x:Shared` kódu v objektovém modelu WPF; lze jej zadat pouze v použití XAML a musí být zpracovány buď výchozí wpf chování nebo v zprostředkující xaml uzel proudu na cestě zatížení, pokud jsou zpracovány pomocí .NET XAML Services a jeho XAML čtečky.

Scénář pro `x:Shared="false"` je, pokud <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkContentElement> definujete nebo odvozené třídy jako prostředek a potom zavést prostředek prvku do modelu obsahu. `x:Shared="false"`umožňuje prostředek prvku, který má být zaveden vícekrát <xref:System.Windows.Controls.UIElementCollection>ve stejné kolekci (například ). Bez `x:Shared="false"` tohoto je neplatný, protože kolekce vynucuje jedinečnost jeho obsahu. Chování však `x:Shared="false"` vytvoří jinou identickou instanci prostředku namísto vrácení stejné instance.

Jiný scénář `x:Shared="false"` pro je, <xref:System.Windows.Freezable> pokud používáte prostředek pro hodnoty animace, ale chcete upravit prostředek na základě animace.

Zpracování `false` řetězce není rozlišována malá a velká písmena.

V WPF, `x:Shared` je platný pouze za následujících podmínek:

- Který <xref:System.Windows.ResourceDictionary> obsahuje položky `x:Shared` s musí být zkompilován. Nemůže <xref:System.Windows.ResourceDictionary> být v rámci volné XAML nebo použít pro motivy.

- Položka, <xref:System.Windows.ResourceDictionary> která obsahuje položky, nesmí <xref:System.Windows.ResourceDictionary>být vnořena do jiného . Například nelze použít `x:Shared` pro položky <xref:System.Windows.ResourceDictionary> v, <xref:System.Windows.Style> která je <xref:System.Windows.ResourceDictionary> v rámci, která je již položka.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.ResourceDictionary>
- [Zdroje XAML](../fundamentals/xaml-resources-define.md)
- [Základní elementy](../../framework/wpf/advanced/base-elements.md)
