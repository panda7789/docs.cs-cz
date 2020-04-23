---
title: x:Subclass – direktiva
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071365"
---
# <a name="xsubclass-directive"></a>x:Subclass – direktiva

Upravuje chování kompilace značek XAML, pokud `x:Class` je také k dispozici. Namísto vytváření částečné třídy, `x:Class`která je `x:Class` založena na , zadaný je vytvořen jako zprostředkující třídy a pak za předpokladu, odvozené třídy se očekává, že bude založena na `x:Class`.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`namespace`|Nepovinný parametr. Určuje obor názvů CLR, `classname`který obsahuje . Pokud `namespace` je zadán, tečka (.) odděluje `namespace` a `classname`.|
|`classname`|Povinná hodnota. Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro tento XAML. Viz Poznámky.|
|`subclassNamespace`|Nepovinný parametr. Může se `namespace` lišit od toho, pokud každý obor názvů může přeložit druhý. Určuje obor názvů CLR, `subclassName`který obsahuje . Pokud `subclassName` je zadán, tečka (.) odděluje `subclassNamespace` a `subclassName`.|
|`subclassName`|Povinná hodnota. Určuje název CLR podtřídy.|

## <a name="dependencies"></a>Závislosti

[x:Class Directive](xclass-directive.md) musí být také k dispozici na stejném objektu a tento objekt musí být kořenovým prvkem výroby XAML.

## <a name="remarks"></a>Poznámky

`x:Subclass`použití je primárně určeno pro jazyky, které nepodporují deklarace dílčí třídy.

Třída použitá `x:Subclass` jako vnořená třída `x:Subclass` nemůže být vnořenou a musí odkazovat na kořenový objekt, jak je vysvětleno v části "Závislosti".

V opačném případě `x:Subclass` koncepční význam je nedefinována implementací služby .NET XAML Services. Důvodem je, že chování služby .NET XAML Services neurčuje celkový programovací model, podle kterého jsou připojeny značky XAML a kód zálohování. Implementace dalších konceptů `x:Class` souvisejících s a `x:Subclass` jsou prováděny konkrétní mise, které používají programovací modely nebo aplikační modely k definování, jak připojit značky XAML, zkompilované značky a kód založený na CLR. Každý rámec může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní součásti, které musí být zahrnuty v prostředí sestavení. V rámci akce sestavení se také může lišit v závislosti na konkrétní jazyk CLR, který se používá pro kód na pozadí.

## <a name="wpf-usage-notes"></a>Poznámky k použití WPF

`x:Subclass`může být na kořenové <xref:System.Windows.Application> stránce nebo na kořenovém `x:Class`adresáři v definici aplikace, která již má . Deklarování `x:Subclass` na libovolný prvek než kořen stránky nebo `x:Class` aplikace nebo určení, kde neexistuje, způsobí chybu v době kompilace.

Vytvoření odvozené třídy, `x:Subclass` které pracují správně pro scénář je poměrně složité. Možná budete muset prozkoumat zprostředkující soubory (soubory G vytvořené ve složce obj projektu podle kompilace značek s názvy, které obsahují názvy souborů XAML). Tyto zprostředkující soubory vám mohou pomoci určit původ určitých programovacích konstrukcí ve spojených částečných třídách v kompilované aplikaci.

Obslužné rutiny událostí `internal override` `Friend Overrides` v odvozené třídě musí být (v jazyce Microsoft Visual Basic) k přepsání zástupných procedur pro obslužné rutiny, jak byly vytvořeny v zprostředkující třídě během kompilace. V opačném případě odvozené implementace třídy skrýt (stín) implementace zprostředkující třídy a zprostředkující třídy obslužné rutiny nejsou vyvolány.

Při definování `x:Class` obou `x:Subclass`a , není nutné zadat žádnou implementaci pro `x:Class`třídu, na kterou odkazuje . Stačí dát název prostřednictvím atributu `x:Class` tak, aby kompilátor má některé pokyny pro třídu, kterou vytvoří v zprostředkující soubory (kompilátor nevybere výchozí název v tomto případě). Můžete dát `x:Class` třídy implementace; však toto není typický scénář `x:Class` `x:Subclass`pro použití obou a .

## <a name="see-also"></a>Viz také

- [x:Class – direktiva](xclass-directive.md)
- [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
