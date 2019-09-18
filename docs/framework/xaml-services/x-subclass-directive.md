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
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053915"
---
# <a name="xsubclass-directive"></a>x:Subclass – direktiva
Upraví chování kompilace značek XAML `x:Class` , když je také k dispozici. Namísto vytvoření částečné třídy, která je založena na `x:Class`, je poskytnuto `x:Class` vytvoření jako zprostředkující třída, a poté je `x:Class`očekávána vaše poskytnutá odvozená třída na základě.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelný parametr. Určuje obor názvů CLR, který `classname`obsahuje. Je `namespace` -li parametr zadán, bude znak tečky ( `namespace` . `classname`) oddělen a.|  
|`classname`|Povinný parametr. Určuje název CLR částečné třídy, která spojuje načtený XAML a váš kód na pozadí pro daný XAML. Viz poznámky.|  
|`subclassNamespace`|Volitelný parametr. Může se lišit od `namespace` , pokud každý obor názvů dokáže vyřešit jiné. Určuje obor názvů CLR, který `subclassName`obsahuje. Je `subclassName` -li parametr zadán, bude znak tečky ( `subclassNamespace` . `subclassName`) oddělen a.|  
|`subclassName`|Povinný parametr. Určuje název CLR podtřídy.|  
  
## <a name="dependencies"></a>Závislosti  
 [direktiva x:Class](x-class-directive.md) musí být také zadána u stejného objektu a tento objekt musí být kořenovým elementem výroby XAML.  
  
## <a name="remarks"></a>Poznámky  
 `x:Subclass`použití je primárně určeno pro jazyky, které nepodporují deklarace částečné třídy.  
  
 Třída použitá jako `x:Subclass` nemůže být vnořená třída a `x:Subclass` musí odkazovat na kořenový objekt, jak je vysvětleno v části závislosti.  
  
 V opačném případě konceptuální význam `x:Subclass` není definován .NET Framework implementaci služby XAML. Důvodem je to, že .NET Framework chování služby XAML neurčuje celkový programovací model, pomocí kterého jsou kódy XAML a back-Code připojeny. Implementace dalších konceptů vztahujících `x:Class` se `x:Subclass` k a jsou prováděny konkrétními rozhraními, která používají programovací modely nebo aplikační modely k definování způsobu propojení kódu XAML, kompilovaných značek a kódu založeného na CLR na pozadí. Každé rozhraní může mít vlastní akce sestavení, které umožňují některé chování nebo konkrétní komponenty, které musí být součástí prostředí sestavení. V rámci rozhraní se akce sestavení mohou lišit také podle konkrétního jazyka CLR, který je použit pro kód na pozadí.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 `x:Subclass`může být v kořenu stránky nebo <xref:System.Windows.Application> kořenovém adresáři v definici aplikace, která již má. `x:Class` Deklarace `x:Subclass` na jakýkoli element jiný než stránka nebo kořen aplikace nebo jeho určení, `x:Class` Pokud neexistuje, způsobí chybu při kompilaci.  
  
 Vytváření odvozených tříd, které jsou pro `x:Subclass` daný scénář správně fungovat, je poměrně složité. Je možné, že budete muset prozkoumávat mezilehlé soubory (soubory. g vytvořené ve složce obj projektu pomocí kódu zkompiluje s názvy, které obsahují názvy souborů. XAML). Tyto mezilehlé soubory vám pomohou určit původ určitých programovacích konstrukcí v připojených částečných třídách v kompilované aplikaci.  
  
 Obslužné rutiny událostí v odvozené třídě musí `internal override` být`Friend Overrides` (v Microsoft Visual Basic), aby bylo možné přepsat zástupné procedury pro obslužné rutiny, jak jsou vytvořeny v zprostředkující třídě během kompilace. V opačném případě implementací odvozené třídy skryje (stín) implementaci zprostředkující třídy a obslužné rutiny zprostředkující třídy nejsou vyvolány.  
  
 Při definování `x:Class` a `x:Subclass`není nutné poskytovat žádnou implementaci pro `x:Class`třídu, na kterou odkazuje. Stačí mu dát název prostřednictvím `x:Class` atributu, aby měl kompilátor nějaké pokyny pro třídu, kterou vytvoří v zprostředkujících souborech (kompilátor v tomto případě nevybere výchozí název). `x:Class` Třídu můžete přidělit implementaci, ale to není Typický scénář pro `x:Class` použití a `x:Subclass`.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
