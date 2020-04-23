---
title: x:Class – direktiva
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072037"
---
# <a name="xclass-directive"></a>x:Class – direktiva
Konfiguruje kompilaci značek XAML tak, aby spojovala částečné třídy mezi značkami a kódem na pozadí. Částečná třída kódu je definována v samostatném souboru kódu v jazyce CLS (Common Language Specification), zatímco částečná třída značek je obvykle vytvořena generováním kódu během kompilace XAML.

## <a name="xaml-attribute-usage"></a>Použití atributu XAML

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>Hodnoty XAML

|||
|-|-|
|`namespace`|Nepovinný parametr. Určuje obor názvů CLR, který obsahuje `classname`částečnou třídu identifikovanou programem . Pokud `namespace` je zadán, tečka (.) odděluje `namespace` a `classname`. Viz Poznámky.|
|`classname`|Povinná hodnota. Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro tento XAML.|

## <a name="dependencies"></a>Závislosti

`x:Class`lze zadat pouze na kořenovém prvku výroby XAML. `x:Class`je neplatný u libovolného objektu, který má nadřazený objekt v produkci XAML. Další informace naleznete [ \[v oddíle\] 4.3.1.6 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Poznámky

Hodnota `namespace` může obsahovat další tečky pro uspořádání souvisejících oborů názvů do hierarchií názvů, což je běžná technika v programování rozhraní .NET. Pouze poslední tečka v `x:Class` řetězci hodnot je `namespace` `classname.` interpretována k oddělení `x:Class` a Třída, která se používá jako nemůže být vnořené třídy. Vnořené třídy nejsou povoleny, protože `x:Class` určení významu teveřů pro řetězce je nejednoznačné, pokud jsou povoleny vnořené třídy.

V existujících programovacích modelů, které používají `x:Class`, `x:Class` je volitelné v tom smyslu, že je zcela platný mít stránku XAML, která nemá žádný kód na pozadí. Tato schopnost však spolupracuje s akcemi sestavení implementovanými rámci, které používají XAML. `x:Class`schopnost je také ovlivněna rolemi, které mají různé klasifikace obsahu určeného zadaným v XAML v aplikačním modelu a v odpovídajících akcích sestavení. Pokud vaše XAML deklaruje hodnoty atributů zpracování událostí nebo instanci vlastní prvky, kde `x:Class` jsou definující třídy ve třídě s kódem na pozadí, je třeba zadat odkaz směrnice (nebo [x:Subclass](xsubclass-directive.md)) na příslušnou třídu pro kód na pozadí.

Hodnota `x:Class` směrnice musí být řetězec, který určuje plně kvalifikovaný název třídy, ale bez <xref:System.Type.FullName%2A?displayProperty=nameWithType>informací o sestavení (ekvivalentní ). Pro jednoduché aplikace můžete vynechat informace o oboru názvů CLR, pokud je kód na pozadí také strukturován tímto způsobem (definice kódu začíná na úrovni třídy).

Soubor s kódem na pozadí pro definici stránky nebo aplikace musí být v rámci souboru kódu, který je součástí projektu, který vytváří kompilovanou aplikaci a zahrnuje kompilaci značek. Pro třídy CLR je nutné dodržovat pravidla názvů. Další informace naleznete [v tématu Pokyny k návrhu rámce](../../../api/index.md). Ve výchozím nastavení musí být `public`třída kód na pozadí ; můžete ji však definovat na jiné úrovni přístupu pomocí [direktivy x:ClassModifier .](xclassmodifier-directive.md)

Tento výklad `x:Class` atributu se vztahuje pouze na implementaci XAML založenou na CLR, zejména na služby .NET XAML. Jiné implementace XAML, které nejsou založeny na CLR a které nepoužívají služby .NET XAML, mohou pro připojení značek XAML a záložního kódu za běhu použít jiný vzorec rozlišení. Další informace o obecnějších `x:Class`interpretacích aplikace naleznete v tématu [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

Na určité úrovni architektury `x:Class` význam je nedefinovaný v .NET XAML Services. Důvodem je, že služba .NET XAML Services neurčuje programovací model, podle kterého jsou připojeny značky XAML a kód zálohování. Další použití `x:Class` směrnice může být implementováno konkrétní rozhraní, které používají programovací modely nebo modely aplikací k definování, jak připojit značky XAML a kód na pozadí clr. Každý rámec může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní součásti, které musí být zahrnuty v prostředí sestavení. V rámci akce sestavení se také může lišit v závislosti na konkrétní jazyk CLR, který se používá pro kód na pozadí.

## <a name="xclass-in-the-wpf-programming-model"></a>x:Třída v programovacím modelu WPF

V aplikacích WPF a modelu `x:Class` aplikace WPF lze deklarovat jako atribut pro každý prvek, který je kořenem souboru XAML a `Page` je kompilován <xref:System.Windows.Application> (kde je XAML zahrnuta v projektu aplikace WPF s akcí sestavení) nebo pro kořen v definici aplikace kompilované aplikace WPF. Deklarování `x:Class` na jiný prvek než kořen stránky nebo kořen aplikace nebo na wpf XAML soubor, který není zkompilován, způsobí chybu v době kompilace v rámci .NET Framework 3.0 a .NET Framework 3.5 WPF XAML kompilátor. Informace o dalších `x:Class` aspektech zpracování v WPF naleznete v [tématu Code-Behind a XAML v WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="xclass-for-windows-workflow-foundation"></a>x:Třída pro Windows Workflow Foundation
Pro Windows Workflow `x:Class` Foundation pojmenuje třídu vlastní aktivity složené výhradně v XAML nebo názvy částečné třídy stránky XAML pro návrháře aktivit s kódem na pozadí.

## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight

`x:Class`pro Program Silverlight je dokumentován samostatně. Další informace naleznete v [tématu XAML Namespace (x:) Jazykové funkce (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Viz také

- [x:Subclass – direktiva](xsubclass-directive.md)
- [XAML a vlastní třídy pro WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier – direktiva](xclassmodifier-directive.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
