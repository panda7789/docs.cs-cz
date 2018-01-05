---
title: "x:Code – vnitřní typ jazyka XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d39249a5d1c0e230d21e6d889b92d0b57c98e2ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code – vnitřní typ jazyka XAML
Umožňuje, aby umísťování kódu v rámci provozní XAML. Takový kód můžete buď zkompilují žádnou implementaci procesoru XAML kompilovaný XAML nebo vlevo v produkčním prostředí XAML pro pozdější použití například výklad o modulu runtime.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód v rámci `x:Code` element direktivy jazyka XAML je stále interpretovat v rámci obecné obor názvů XML a obory názvů jazyka XAML zadat. Proto je obvykle potřeba uzavřete kód použitý pro `x:Code` uvnitř `CDATA` segmentu.  
  
 `x:Code`není povoleno pro všechny možné nasazení mechanismy provozních XAML. V konkrétní rozhraní (například WPF) musí být zkompilovány kód. V jiných rozhraní `x:Code` využití může obecně zakázán.  
  
 Pro rozhraní, které umožňují spravované `x:Code` obsahu, kompilátoru správný jazyk pro `x:Code` obsah je dáno nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.  
  
## <a name="wpf-usage-notes"></a>Poznámky pro použití WPF  
 Kód deklarované v rámci `x:Code` pro WPF má několik upozorňují na důležité omezení:  
  
-   `x:Code` – Element direktivy musí být okamžitou podřízený prvek kořenového prvku provozních XAML.  
  
-   [x: Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md) je třeba zadat v kořenovém elementu nadřazené.  
  
-   Kód umístit `x:Code` nakládáno kompilace musí být v rozsahu částečné třídy, která už se vytváří této stránky XAML. Proto všechny kódu, které definujete musí být členy nebo proměnné částečné třídy.  
  
-   Nelze definovat další třídy, jiné než pomocí vnoření třídu uvnitř třídu (vnoření je povoleno, ale není typické, že vnořené třídy nelze odkazovat v jazyce XAML). Obory názvů CLR než obor názvů, který se používá pro existující třídu nelze definované nebo přidat do.  
  
-   Odkazy na entity kód mimo obor názvů třídu CLR musí být plně kvalifikovaný. Členové se deklarovat jsou přepsání přepisovatelné členům třídu, musí zadat pomocí klíčového slova přepsání konkrétní jazyk. Pokud deklarované členy v `x:Code` oboru v konfliktu s členové třídu vytvořený mimo XAML, tak, že kompilátor sestavy konflikt, souboru XAML nelze zkompilovat nebo zatížení.  
  
## <a name="see-also"></a>Viz také  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Podkladový kód a kód XAML v subsystému WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
