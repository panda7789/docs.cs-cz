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
ms.openlocfilehash: 7e6a2379640d2556b553d14d20398a0a14931393
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566805"
---
# <a name="xclass-directive"></a>x:Class – direktiva
Nakonfiguruje kompilace kódu XAML pro připojení částečné třídy mezi značek a kódu. Třídu kódu je definována v samostatném souboru kódu v [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] jazyka, zatímco třídu kód se obvykle vytvoří pomocí generování kódu během kompilace XAML.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelné. Určuje [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] obor názvů, který obsahuje třídu identifikovaný `classname`. Pokud `namespace` není zadaný, tečku (.) odděluje `namespace` a `classname`. V části poznámky.|  
|`classname`|Požadováno. Určuje, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] názvem částečné třídy, která se připojuje načíst XAML a vaše kódu pro tento jazyk XAML.|  
  
## <a name="dependencies"></a>Závislosti  
 `x:Class` lze zadat pouze v kořenovém elementu provozních XAML. `x:Class` je neplatný na libovolný objekt, který má nadřazený prvek v produkčním prostředí XAML. Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 `namespace` Hodnota může obsahovat další tečky uspořádat související obory názvů do názvu hierarchií, což je běžný postup při programování pro rozhraní .NET Framework. Pouze poslední tečky v řetězec `x:Class` hodnoty interpretována k oddělení `namespace` a `classname.` třídu, která se používá jako `x:Class` nemůže být vnořená třída. Vnořené třídy nejsou povoleny, protože určení význam teček pro `x:Class` řetězce je nejednoznačné, pokud jsou povolena vnořené třídy.  
  
 Ve stávající programovací modely, které používají `x:Class`, `x:Class` je v tom smyslu, že je zcela platné tak, aby měl stránky XAML, který nemá žádné kódu volitelné. Tuto funkci však komunikuje s akcemi sestavení jak je implementované rozhraní, které používají XAML. `x:Class` funkce je ovlivněny také role, že různé klasifikace zadaný XAML obsahu ve model aplikace a v příslušné akce sestavení. Pokud vaše XAML deklaruje atribut zpracování událostí hodnoty nebo vytvoří vlastní elementy, kde definující třídy jsou ve třídě kódu, je nutné zadat `x:Class` direktivy odkaz (nebo [x: Subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) do příslušná třída pro kódu.  
  
 Hodnota `x:Class` – direktiva musí být řetězec, který určuje plně kvalifikovaný název třídy, ale bez jakýchkoli informací sestavení (ekvivalentní <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pro jednoduché aplikace můžete vynechat údaje obor názvů CLR, pokud jsou kódu je také strukturovaná této způsobem (kód definice se zahájí na úrovni třídy).  
  
 V souboru kódu definici stránky nebo aplikace musí být v souboru kódu, který je součástí projekt, který vytváří kompilované aplikace a zahrnuje kompilace kódu. Postupujte podle pravidla pro názvy pro třídy CLR. Další informace najdete v tématu [pokynů pro návrh Framework](../../../docs/standard/design-guidelines/index.md). Ve výchozím nastavení, musí být třída kódu `public`; ale můžete ji definovat na úrovni různý přístup pomocí [x: ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
 Tento výklad `x:Class` atribut platí pouze pro implementaci na základě CLR XAML, zejména pro rozhraní .NET Framework XAML Services. Jiné XAML implementace, které nejsou založené na modulu CLR a která nepoužívají rozhraní .NET Framework XAML Services může pomocí různých řešení vzorce pro propojení XAML značek a kódu v době spuštění zálohování. Další informace o další obecné interpretace z `x:Class`, najdete v části [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Na určité úrovni architektury význam `x:Class` není definována v rozhraní .NET Framework XAML Services. Je to proto, že rozhraní .NET Framework XAML Services neurčuje programovací model, ve které XAML značek a kódu zálohování připojeni. Další využití `x:Class` – direktiva může implementovat určité rozhraní, kterých programovací modely nebo modely aplikace a definovat, jak připojit kód XAML a na základě CLR kódu. Každý framework může mít svůj vlastní akce sestavení, které povolit některé chování nebo konkrétní součásti, které musí být součástí prostředí sestavení. V rámci rozhraní akce sestavení se mohou lišit v závislosti na konkrétní jazyk CLR, který se používá pro modelu code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x: Class – v modelu programování WPF  
 V aplikacích WPF a model aplikace WPF `x:Class` lze deklarovat jako atribut pro libovolný element, který je kořenem souboru XAML a se kompiluje (kde je XAML zahrnutý v projektu aplikace WPF s `Page` akce sestavení), nebo < C4 > <xref:System.Windows.Application>  kořenové v definici aplikace kompilované aplikace WPF. Deklarování `x:Class` na element než stránky kořenové nebo kořenový adresář aplikace, nebo soubor WPF XAML, který není kompilovat, způsobí chybu kompilace v části [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] a [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] kompilátoru WPF XAML. Informace o dalších aspektů `x:Class` zpracování v grafickém subsystému WPF, najdete v části [kódu a XAML v grafickém subsystému WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x: Class – pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Class` názvy třídu vlastní aktivita tvoří zcela v jazyce XAML, nebo názvy třídu stránky XAML pro Návrhář aktivity s kódem v pozadí.  
  
## <a name="silverlight-usage-notes"></a>Poznámky pro použití programu Silverlight  
 `x:Class` pro Silverlight je popsána samostatně. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Viz také  
 [x:Subclass – direktiva](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [XAML a vlastní třídy pro WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier – direktiva](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
