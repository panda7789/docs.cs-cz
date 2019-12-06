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
ms.openlocfilehash: d6baa6d8eb3a6d3520fb1549e2182f27ca52c36a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837243"
---
# <a name="xclass-directive"></a>x:Class – direktiva
Konfiguruje kompilaci kódu XAML pro spojování dílčích tříd mezi značkami a kódem na pozadí. Částečná třída Code je definována v samostatném souboru kódu v jazyce CLS (Common Language Specification), zatímco částečná třída značek je obvykle vytvořena generováním kódu během kompilace XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelné. Určuje obor názvů CLR, který obsahuje částečnou třídu identifikovanou `classname`. Je-li zadán `namespace`, znak tečky (.) odděluje `namespace` a `classname`. Viz poznámky.|  
|`classname`|Požadováno. Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro daný XAML.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:Class` lze zadat pouze pro kořenový element výroby XAML. `x:Class` je neplatný pro libovolný objekt, který má nadřazenou položku v produkci XAML. Další informace naleznete v tématu [\[MS-XAML\] oddílu 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `namespace` může obsahovat další tečky pro uspořádání souvisejících oborů názvů do hierarchií názvů, což je běžná technika v .NET Framework programování. Pouze poslední tečka v řetězci hodnot `x:Class` je interpretována jako oddělit `namespace` a `classname.` třída, která je použita jako `x:Class` nemůže být vnořená třída. Vnořené třídy nejsou povoleny, protože určení významu teček pro `x:Class` řetězců je nejednoznačné, pokud jsou vnořené třídy povoleny.  
  
 V existujících programovacích modelech, které používají `x:Class`, `x:Class` je volitelný v tom smyslu, že je zcela platný pro stránku XAML, která nemá žádný kód na pozadí. Tato funkce však komunikuje s akcemi sestavení, jak jsou implementovány rozhraními, které používají XAML. funkce `x:Class` je také ovlivněna rolemi, které mají různé klasifikace obsahu v jazyce XAML, v modelu aplikace a odpovídajících akcích sestavení. Pokud váš kód XAML deklaruje hodnoty atributů zpracování událostí nebo vytváří instance vlastních prvků, kde jsou definiční třídy v třídě kódu na pozadí, je nutné zadat odkaz na direktivu `x:Class` (nebo [x:Subclass –](x-subclass-directive.md)) na odpovídající třídu pro kód na pozadí.  
  
 Hodnota direktivy `x:Class` musí být řetězec, který určuje plně kvalifikovaný název třídy, ale bez informací o sestavení (ekvivalentní <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pro jednoduché aplikace můžete vynechat informace oboru názvů CLR, pokud je kód na pozadí strukturovaný i v tomto způsobem (definice kódu začíná na úrovni třídy).  
  
 Soubor kódu na pozadí definice stránky nebo aplikace musí být v rámci souboru kódu, který je součástí projektu, který vytváří kompilovaná aplikace a zahrnuje kompilaci kódu. Pro třídy CLR je nutné dodržovat pravidla názvu. Další informace najdete v tématu [pokyny pro návrh rozhraní](../../standard/design-guidelines/index.md). Ve výchozím nastavení musí být třída kódu na pozadí `public`; můžete ji však definovat na jiné úrovni přístupu pomocí [direktivy x:ClassModifier –](x-classmodifier-directive.md).  
  
 Tato interpretace atributu `x:Class` platí pouze pro implementaci XAML založenou na CLR, zejména pro .NET Framework XAML Services. Jiné implementace jazyka XAML, které nejsou založené na modulu CLR a které nepoužívají .NET Framework služby XAML, mohou použít jiný vzorec rozlišení pro připojení kódu XAML a záložního běhového kódu. Další informace o obecných výkladech `x:Class`naleznete v tématu [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 V určité úrovni architektury není význam `x:Class` v .NET Frameworkch službách XAML definován. Důvodem je to, že .NET Framework služby XAML neurčuje programovací model, pomocí kterého se připojovat kód XAML a back-Code. Další použití direktivy `x:Class` může být implementováno konkrétními rozhraními, která používají programovací modely nebo aplikační modely k definování způsobu připojení kódu XAML a kódu založeného na CLR. Každé rozhraní může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní komponenty, které musí být součástí prostředí sestavení. V rámci rozhraní se akce sestavení mohou lišit také v závislosti na konkrétním jazyce CLR, který se používá pro kód na pozadí.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x:Class v programovacím modelu WPF  
 V aplikacích WPF a modelu aplikace WPF lze `x:Class` deklarovat jako atribut pro libovolný prvek, který je kořenem souboru XAML a je kompilován (kde je XAML obsažena v projektu aplikace WPF s akcí sestavení `Page`), nebo pro <xref:System.Windows.Application> kořen v definici aplikace zkompilované aplikace WPF. Deklarace `x:Class` na jiném prvku než kořen stránky nebo kořen aplikace nebo v souboru XAML WPF, který není zkompilován, způsobí chybu při kompilaci pod kompilátorem .NET Framework 3,0 a .NET Framework 3,5 WPF. Informace o dalších aspektech `x:Class` manipulace s WPF naleznete v tématu [Code-on a XAML v](../wpf/advanced/code-behind-and-xaml-in-wpf.md)subsystému WPF.  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x:Class pro programovací model Windows Workflow Foundation  
 Pro programovací model Windows Workflow Foundation `x:Class` pojmenuje třídu vlastní aktivity složené zcela v jazyce XAML nebo pojmenuje podtřídu stránky XAML pro návrháře aktivit s kódem na pozadí.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Class` pro prostředí Silverlight je zdokumentován samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Viz také:

- [x:Subclass – direktiva](x-subclass-directive.md)
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier – direktiva](x-classmodifier-directive.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
