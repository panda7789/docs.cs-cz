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
ms.openlocfilehash: 5f7b072e90e92070dd7fda2f0ad44814009268b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199450"
---
# <a name="xclass-directive"></a>x:Class – direktiva
Nakonfiguruje kompilace kódu XAML pro připojení mezi značky a modelu code-behind částečné třídy. Kód částečná třída je definována v samostatném souboru kódu v [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] jazyka, zatímco částečné třídy kód se obvykle vytvoří pomocí generování kódu během kompilace XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelné. Určuje [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] obor názvů obsahující částečné třídy identifikovaný `classname`. Pokud `namespace` není zadána, tečku (.) odděluje `namespace` a `classname`. Viz poznámky.|  
|`classname`|Povinný parametr. Určuje, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] název částečné třídy, která se připojuje načíst XAML a vašeho kódu na pozadí pro tento XAML.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:Class` lze zadat pouze na kořenový prvek XAML výroby. `x:Class` není platný na libovolný objekt, který má nadřazený objekt v produkčním prostředí XAML. Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 `namespace` Hodnota může obsahovat další tečky uspořádat související obory názvů do názvu hierarchií, což je běžná technika programování v rozhraní .NET Framework. Pouze poslední tečky v řetězci `x:Class` hodnoty interpretována oddělit `namespace` a `classname.` třídu, která se používá jako `x:Class` nemůže být vnořená třída. Vnořené třídy nejsou povoleny, protože určení význam tečky jako `x:Class` řetězce je nejednoznačný, pokud jsou povolené vnořené třídy.  
  
 V existujícím programovací modely, které používají `x:Class`, `x:Class` je v tom smyslu, že se jedná o platný zcela stránky XAML, který nemá žádné použití modelu code-behind volitelné. Však tato funkce interaguje s akcí sestavení, jako je například implementovaných rozhraní používat XAML. `x:Class` funkce je také ovlivněno rolí, různé klasifikace XAML zadaný obsah v aplikační model a v odpovídající akce sestavení. Pokud vaše XAML deklaruje atribut zpracování událostí hodnot nebo vytvoří vlastní elementy kde definující třídy jsou ve třídě použití modelu code-behind, je nutné zadat `x:Class` direktiv odkazu (nebo [x: Subclass](x-subclass-directive.md)) k příslušné třídy pro použití modelu code-behind.  
  
 Hodnota `x:Class` direktiva musí být řetězec, který určuje plně kvalifikovaný název třídy, ale bez jakýchkoli informací o sestavení (odpovídá <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pro jednoduché aplikace můžete vynechat informace obor názvů CLR, pokud modelu code-behind také strukturovaná této způsobem (spustí definice kódu na úrovni třídy).  
  
 Soubor kódu na pozadí pro definici stránky nebo aplikace musí být v souboru kódu, který se dodává jako součást projektu, který vytváří kompilovanou aplikaci a zahrnuje kompilace označení. Je třeba dodržovat pravidla pro názvy tříd CLR. Další informace najdete v tématu [pokyny k návrhu architektury](../../standard/design-guidelines/index.md). Ve výchozím nastavení, musí být třída použití modelu code-behind `public`; nicméně, můžete ji definovat na úrovni různý přístup s použitím [x: ClassModifier – direktiva](x-classmodifier-directive.md).  
  
 Toto vyhodnocení `x:Class` atributu platí pouze pro provedení na základě CLR XAML, zejména pro rozhraní .NET Framework XAML Services. V jiných implementacích XAML, která nejsou založena na modulu CLR a, která nepoužívají rozhraní .NET Framework XAML Services může používat jiné řešení vzorec pro připojování značky XAML a zálohování za běhu kódu. Další informace o interpretaci obecnější `x:Class`, naleznete v tématu [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Na určité úrovni architektury význam `x:Class` není definovaná v rozhraní .NET Framework XAML Services. Je to proto, že rozhraní .NET Framework XAML Services neurčuje programovací model, ve které XAML jsou připojené značek a kódu zálohování. Další způsoby použití `x:Class` směrnice může implementovat určité rozhraní, které používají programovací modely nebo aplikačních modelů pro definování připojení značky XAML a na základě CLR kódu na pozadí. Každé rozhraní, může mít svůj vlastní akce sestavení, které umožňují některé chování nebo konkrétní součásti, které musí být součástí prostředí pro sestavení. V rámci akce sestavení také může lišit v závislosti na konkrétní jazyk CLR, který se používá pro modelu code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class v programovací Model WPF  
 V aplikacích WPF a aplikační model WPF `x:Class` mohou být deklarovány jako atribut pro libovolný element, který je kořenem souboru XAML a je kompilovaný (kde je zahrnuta XAML v projektu aplikace WPF s `Page` akce sestavení), nebo < C4 > <xref:System.Windows.Application>  kořen v definici aplikace kompilovanou aplikaci WPF. Deklarování `x:Class` na element než kořenové stránky nebo kořenový adresář aplikace, nebo WPF XAML soubor, který se zkompiluje, způsobí chybu kompilace v části [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] a [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] kompilátoru WPF XAML. Informace o dalších aspektech `x:Class` zpracování v subsystému WPF naleznete v tématu [použití modelu Code-Behind a XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Class` názvy třídy vlastní aktivity skládá zcela v XAML nebo názvy částečné třídy stránky XAML pro Návrhář aktivity s kódem na pozadí.  
  
## <a name="silverlight-usage-notes"></a>Poznámky k použití aplikace Silverlight  
 `x:Class` pro prostředí Silverlight je zdokumentován samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také:

- [x:Subclass – direktiva](x-subclass-directive.md)
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier – direktiva](x-classmodifier-directive.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
