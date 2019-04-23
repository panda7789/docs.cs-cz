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
ms.openlocfilehash: 850fe8acf9e47149bd385e78b30e04ba77d7a8b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59140787"
---
# <a name="xsubclass-directive"></a>x:Subclass – direktiva
Upravuje chování kompilace kódu XAML při `x:Class` je také k dispozici. Místo vytváření částečnou třídu, která je založena na `x:Class`, poskytnutého `x:Class` je vytvořen jako zprostředkující třída, a pak se očekává na základě zadané odvozené třídy `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelné. Určuje obor názvů CLR, který obsahuje `classname`. Pokud `namespace` není zadána, tečku (.) odděluje `namespace` a `classname`.|  
|`classname`|Povinný parametr. Určuje název CLR částečné třídy, která se připojuje načíst XAML a vašeho kódu na pozadí pro tento XAML. Viz poznámky.|  
|`subclassNamespace`|Volitelné. Může se lišit od `namespace` pokud každý obor názvů lze vyřešit druhé. Určuje obor názvů CLR, který obsahuje `subclassName`. Pokud `subclassName` není zadána, tečku (.) odděluje `subclassNamespace` a `subclassName`.|  
|`subclassName`|Povinný parametr. Určuje název CLR podtřídy.|  
  
## <a name="dependencies"></a>Závislosti  
 [x: Class – direktiva](x-class-directive.md) musí se poskytnout i na stejný objekt, a tento objekt musí být kořenovým prvkem produkční XAML.  
  
## <a name="remarks"></a>Poznámky  
 `x:Subclass` využití je primárně určena pro jazyky, které nepodporují deklarace částečné třídy.  
  
 Třída, která slouží jako `x:Subclass` nemůže být vnořené třídy a `x:Subclass` musí odkazovat na kořenový objekt, jak je popsáno v části "Závislosti".  
  
 V opačném případě koncepční význam `x:Subclass` není definovaná implementací rozhraní .NET Framework XAML Services. Je to proto, že rozhraní .NET Framework XAML Services chování neurčuje celkový programovací model, ve které XAML jsou připojené značek a kódu zálohování. Implementace další koncepty související s `x:Class` a `x:Subclass` provádí určité rozhraní, které používají programovací modely nebo aplikačních modelů pro definování připojení značky XAML, zkompilovaný kód a na základě CLR kódu na pozadí. Každé rozhraní, může mít svůj vlastní akce sestavení, které umožňují některé chování nebo konkrétní součásti, které musí být součástí prostředí pro sestavení. V rámci akce sestavení může také záviset na konkrétní jazyk CLR, který se používá pro modelu code-behind.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 `x:Subclass` může být na kořenovém adresáři stránku nebo na <xref:System.Windows.Application> kořen v definici aplikace, která už má `x:Class`. Deklarování `x:Subclass` u libovolného elementu než kořenové stránky nebo aplikace, nebo pokud jeho zadáním `x:Class` existuje, způsobí chybu kompilace.  
  
 Vytváření odvozené třídy, které pracují správně `x:Subclass` scénář je poměrně složitý. Můžete potřebovat k prozkoumání zprostředkující soubory (soubory .g vytvářených značky kompilace s názvy, které zahrnují názvy souborů XAML v složku obj projektu). Tyto zprostředkující soubory můžete určit původ některé programovací konstrukce v připojeném k částečné třídy v kompilované aplikaci.  
  
 Obslužné rutiny událostí v odvozené třídě musí být `internal override` (`Friend Overrides` v aplikaci Microsoft Visual Basic) za účelem přepsání zástupné procedury pro obslužné rutiny, jak ho vytvořila zprostředkující třída během kompilace. V opačném případě implementace odvozené třídy skryje (stínové) zprostředkující třída implementace a nejsou vyvolány zprostředkující třída obslužné rutiny.  
  
 Při definování obě `x:Class` a `x:Subclass`, není potřeba poskytovat žádné implementace třídy, který je odkazován `x:Class`. Je potřeba jenom s názvem prostřednictvím `x:Class` atribut tak, aby kompilátor má některé pokyny pro třídu, která vytvoří v mezilehlé soubory (kompilátor není vyberte výchozí název v tomto případě). Můžete poskytnout `x:Class` třídy implementace, ale to není Typický scénář použití obou `x:Class` a `x:Subclass`.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
