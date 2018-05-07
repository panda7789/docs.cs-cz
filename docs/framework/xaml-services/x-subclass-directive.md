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
ms.openlocfilehash: b04982ff0b7685b4e4b809255e3bbe541b42cb9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xsubclass-directive"></a>x:Subclass – direktiva
Mění chování kompilace kódu XAML při `x:Class` k dispozici je také. Místo vytváření částečné třídu, která je založena na `x:Class`, poskytnutého `x:Class` je vytvořen jako zprostředkující třída, a pak se očekává založeny na vaše zadané odvozené třídy `x:Class`.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`namespace`|Volitelné. Určuje CLR obor názvů, který obsahuje `classname`. Pokud `namespace` není zadaný, tečku (.) odděluje `namespace` a `classname`.|  
|`classname`|Požadováno. Určuje název CLR částečné třídy, který se připojuje načíst XAML a vaše kódu pro tento jazyk XAML. V části poznámky.|  
|`subclassNamespace`|Volitelné. Může lišit od `namespace` pokud každý obor názvů můžete vyřešit dalších. Určuje CLR obor názvů, který obsahuje `subclassName`. Pokud `subclassName` není zadaný, tečku (.) odděluje `subclassNamespace` a `subclassName`.|  
|`subclassName`|Požadováno. Určuje název CLR podtřídy.|  
  
## <a name="dependencies"></a>Závislosti  
 [x: Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md) musí být poskytovány na stejný objekt, a tento objekt musí být kořenový element provozních XAML.  
  
## <a name="remarks"></a>Poznámky  
 `x:Subclass` využití je primárně určený pro jazyky, které nepodporují deklarace třídu.  
  
 Třída, která slouží jako `x:Subclass` nemůže být vnořené třídy a `x:Subclass` musí odkazovat na kořenový objekt, jak je popsáno v části "Závislosti".  
  
 V opačném koncepční význam `x:Subclass` není definována implementací rozhraní .NET Framework XAML Services. Je to proto, že rozhraní .NET Framework XAML Services chování neurčuje celkové programovací model, ve které XAML značek a kódu zálohování připojeni. Implementace další koncepty související s `x:Class` a `x:Subclass` provádí konkrétní architektury, kterých programovací modely nebo modely aplikace a definovat, jak připojit kód XAML, zkompilovaný kód a na základě CLR kódu. Každý framework může mít svůj vlastní akce sestavení, které povolit některé chování nebo konkrétní součásti, které musí být součástí prostředí sestavení. V rámci rozhraní akce sestavení může také lišit v závislosti na konkrétní jazyk CLR, který se používá pro modelu code-behind.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 `x:Subclass` může být v kořenovém adresáři stránku nebo na <xref:System.Windows.Application> kořenové v definici aplikace, která už má `x:Class`. Deklarování `x:Subclass` u libovolného elementu jiného než kořenové stránky nebo aplikace, nebo ho zadáte, kde ne `x:Class` existuje, dojde k chybě kompilace.  
  
 Vytváření odvozené třídy, které pracují správně pro `x:Subclass` scénář je poměrně složitá. Možná bude muset prozkoumat zprostředkující soubory (soubory .g vyprodukované kompilace kódu, s názvy, které zahrnují názvy souborů XAML ve složce obj. projektu). Tyto soubory zprostředkující vám pomohou určit původ určité programovací konstrukce v připojené k částečné třídy kompilované aplikace.  
  
 Obslužné rutiny událostí v odvozené třídě musí být `internal override` (`Friend Overrides` v aplikaci Microsoft Visual Basic) Chcete-li přepsat zástupných procedur u obslužných rutin, jako vytvoří ve třídě zprostředkující během kompilace. Jinak hodnota implementace odvozené třídy skrýt (stínové) implementaci zprostředkující třídy a nejsou volání zprostředkující třídu obslužné rutiny.  
  
 Když definujete obě `x:Class` a `x:Subclass`, není nutné k zajištění všech implementace pro třídu, která je odkazován objektem `x:Class`. Potřebujete pojmenujte ho pomocí `x:Class` atributů tak, aby kompilátor má některé pokyny pro třídu, která vytváří v zprostředkující soubory (kompilátor není vyberte výchozí název v tomto případě). Můžete udělit `x:Class` třídy implementace; je to ale není Typický scénář použití obě `x:Class` a `x:Subclass`.  
  
## <a name="see-also"></a>Viz také  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [XAML a vlastní třídy pro WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
