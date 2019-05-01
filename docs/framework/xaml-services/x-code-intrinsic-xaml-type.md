---
title: x:Code – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971844"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code – vnitřní typ jazyka XAML
Umožňuje umístění kódu v rámci výrobní XAML. Takový kód můžete buď zkompilován s žádnou implementaci procesoru XAML, který zkompiluje XAML nebo doleva v produkčním prostředí XAML pro pozdější použití například interpretace modulem runtime, který.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Poznámky  
 Kód v rámci `x:Code` – element direktivy XAML je stále interpretovány v rámci obecné oboru názvů XML a obory názvů XAML k dispozici. Proto je obvykle nutné uvést kód používá pro `x:Code` uvnitř `CDATA` segmentu.  
  
 `x:Code` pro všechny možné nasazení mechanismy produkce XAML není povolena. V konkrétních platforem (například WPF) musí být kód zkompilován. V další architektury `x:Code` využití může být obecně zakázáno.  
  
 Pro rozhraní, které umožňují spravované `x:Code` obsahu, kompilátor správný jazyk určený pro `x:Code` obsahu je vzhledem k nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.  
  
## <a name="wpf-usage-notes"></a>Poznámky k použití WPF  
 Kód deklarované v rámci `x:Code` pro WPF obsahuje několik významná omezení:  
  
- `x:Code` – Element direktivy musí být bezprostřední podřízený element kořenového elementu XAML výroby.  
  
- [x: Class – direktiva](x-class-directive.md) musí být zadaná na nadřazený kořenový element.  
  
- Kód umístit `x:Code` kompilace musí být v rozsahu částečné třídy, která už se vytváří pro příslušnou stránku XAML se zpracuje. Proto veškerý kód, který definujete musí být členy nebo proměnné částečné třídy.  
  
- Nejde definovat další třídy, jiné než pomocí vnoření třídy uvnitř částečné třídy (vnoření je povoleno, ale není obvyklé, protože vnořené třídy se nedá odkazovat v XAML). Obory názvů CLR než obor názvů, který se používá pro existující částečné třídy nelze definované nebo přidat do.  
  
- Odkazy na entity kód mimo obor názvů CLR částečné třídy musí být plně kvalifikovaný. Pokud jsou členy deklarované přepsání na částečné třídy overridable členy, to musí být zadaný pomocí klíčové slovo override specifické pro jazyk. Pokud členy deklarované v `x:Code` oboru v konfliktu s členy částečné třídy vytvořený mimo XAML, tak, že kompilátor oznámí konfliktu, soubor XAML nelze kompilovat nebo načíst.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
