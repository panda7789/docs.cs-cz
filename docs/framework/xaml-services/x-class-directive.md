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
ms.openlocfilehash: 6e04085db0fa5a4c4170846dc4ac10d0131032a7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053805"
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
|`namespace`|Volitelný parametr. Určuje obor názvů CLR, který obsahuje částečnou třídu identifikovanou `classname`. Je `namespace` -li parametr zadán, bude znak tečky ( `namespace` . `classname`) oddělen a. Viz poznámky.|  
|`classname`|Povinný parametr. Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro daný XAML.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:Class`dá se zadat jenom pro kořenový element výroby XAML. `x:Class`je neplatný pro libovolný objekt, který má nadřazenou položku v produkci XAML. Další informace naleznete v [ \[části MS-XAML\] 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 `namespace` Hodnota může obsahovat další tečky pro uspořádání souvisejících oborů názvů do hierarchií názvů, což je běžná technika při .NET Framework programování. Pouze poslední `x:Class` tečka v řetězci hodnot je interpretována jako oddělená `namespace` a `classname.` třída, která se používá jako `x:Class` nemůže být vnořená třída. Vnořené třídy nejsou povoleny, protože určení významu teček pro `x:Class` řetězce je nejednoznačné, pokud jsou povoleny vnořené třídy.  
  
 V existujících programovacích modelech `x:Class`, `x:Class` které používají, je volitelný v tom smyslu, že je zcela platný pro stránku XAML, která nemá žádný kód na pozadí. Tato funkce však komunikuje s akcemi sestavení, jak jsou implementovány rozhraními, které používají XAML. `x:Class`schopnost je také ovlivněna rolemi, které mají různé klasifikace obsahu zadaného v jazyce XAML, v modelu aplikace a odpovídajících akcích sestavení. Pokud váš kód XAML deklaruje hodnoty atributů zpracování událostí nebo vytváří instance vlastních prvků, kde jsou definiční třídy v třídě kódu na pozadí, je nutné zadat odkaz na `x:Class` direktivu (nebo [x:Subclass –](x-subclass-directive.md)) na příslušnou třídu pro kód na pozadí.  
  
 Hodnota `x:Class` direktivy musí být řetězec, který určuje plně kvalifikovaný název třídy, ale bez informací o sestavení (ekvivalentní <xref:System.Type.FullName%2A?displayProperty=nameWithType>k). Pro jednoduché aplikace můžete vynechat informace oboru názvů CLR, pokud je kód na pozadí strukturovaný i v tomto způsobem (definice kódu začíná na úrovni třídy).  
  
 Soubor kódu na pozadí definice stránky nebo aplikace musí být v rámci souboru kódu, který je součástí projektu, který vytváří kompilovaná aplikace a zahrnuje kompilaci kódu. Pro třídy CLR je nutné dodržovat pravidla názvu. Další informace najdete v tématu [pokyny pro návrh rozhraní](../../standard/design-guidelines/index.md). Ve výchozím nastavení musí být `public`třída kódu na pozadí. můžete ji však definovat na jiné úrovni přístupu pomocí direktivy [x:ClassModifier –](x-classmodifier-directive.md).  
  
 Tato interpretace `x:Class` atributu platí pouze pro implementaci XAML založenou na CLR, zejména pro .NET Framework služby XAML. Jiné implementace jazyka XAML, které nejsou založené na modulu CLR a které nepoužívají .NET Framework služby XAML, mohou použít jiný vzorec rozlišení pro připojení kódu XAML a záložního běhového kódu. Další informace o obecných výkladech `x:Class`pro naleznete v tématu [ \[MS-XAML.\]](https://go.microsoft.com/fwlink/?LinkId=114525)  
  
 V určité úrovni architektury `x:Class` není význam v .NET Frameworkch službách XAML definován. Důvodem je to, že .NET Framework služby XAML neurčuje programovací model, pomocí kterého se připojovat kód XAML a back-Code. Další použití `x:Class` direktivy může být implementováno konkrétními rozhraními, která používají programovací modely nebo aplikační modely k definování způsobu připojení kódu XAML a kódu založeného na CLR. Každé rozhraní může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní komponenty, které musí být součástí prostředí sestavení. V rámci rozhraní se akce sestavení mohou lišit také v závislosti na konkrétním jazyce CLR, který se používá pro kód na pozadí.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x:Class v programovacím modelu WPF  
 V aplikacích WPF a modelu `x:Class` aplikace WPF lze deklarovat jako atribut pro jakýkoli element, který je kořenem souboru XAML a je kompilován (kde je XAML obsažena v projektu aplikace WPF s `Page` akcí sestavení), nebo pro < C4 > <xref:System.Windows.Application>  root v definici aplikace ZKOMPILOVANÉ aplikace WPF. Deklarace `x:Class` na jiný prvek než kořen stránky nebo kořen aplikace nebo v souboru XAML WPF, který není zkompilován, způsobí chybu při kompilaci pod kompilátorem .NET Framework 3,0 a .NET Framework 3,5 WPF XAML. Informace o dalších aspektech zpracování `x:Class` v WPF naleznete v tématu [Code-on a XAML v](../wpf/advanced/code-behind-and-xaml-in-wpf.md)subsystému WPF.  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x:Class pro programovací model Windows Workflow Foundation  
 Pro programovací model Windows Workflow Foundation `x:Class` pojmenuje třídu vlastní aktivity složené zcela v jazyce XAML nebo pojmenuje podtřídu stránky XAML pro návrháře aktivit s kódem na pozadí.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k používání Silverlight  
 `x:Class`Silverlight je dokumentován samostatně. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také:

- [x:Subclass – direktiva](x-subclass-directive.md)
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier – direktiva](x-classmodifier-directive.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
