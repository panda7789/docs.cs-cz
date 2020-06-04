---
title: Statické a pozdní vazby
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding [Visual Basic], Visual Basic compiler
- binding [Visual Basic], late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding [Visual Basic]
- late binding [Visual Basic], Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
ms.openlocfilehash: e8d87e095b7c3104e3a2d66525644d1771ae883e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410629"
---
# <a name="early-and-late-binding-visual-basic"></a>Statické a pozdní vazby (Visual Basic)
Kompilátor Visual Basic provádí proces, který se volá, `binding` když se objekt přiřadí proměnné objektu. Objekt je *časné vazby* , je-li přiřazen k proměnné deklarované jako pro určitý typ objektu. Předčasný vázané objekty umožňují kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace. Například následující fragment kódu deklaruje proměnnou, která bude typu <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Vzhledem k tomu <xref:System.IO.FileStream> , že se jedná o konkrétní typ objektu, je instance přiřazená k `FS` předčasnému vázání.  
  
 Naopak objekt je *pozdní vazba* , pokud je přiřazena proměnné deklarované jako typ `Object` . Objekty tohoto typu můžou uchovávat odkazy na libovolný objekt, ale nemají spoustu výhod objektů s časnou vazbou. Například následující fragment kódu deklaruje proměnnou objektu pro uchování objektu vráceného `CreateObject` funkcí:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Výhody prvotní vazby  
 Pokud je to možné, měli byste použít objekty s časnou vazbou, protože umožňují kompilátoru provádět důležité optimalizace, které přinesou efektivnější aplikace. Objekty s časnou vazbou jsou výrazně rychlejší než objekty s pozdní vazbou a usnadňují čtení a údržbu kódu tím, že přesně udávají, jaký typ objektů se používá. Další výhodou pro předčasné vázání je to, že umožňuje použití užitečných funkcí, jako je automatické dokončování kódu a dynamické pomoci, protože integrované vývojové prostředí (IDE) sady Visual Studio dokáže přesně určit, se kterým typem objektu pracujete při úpravách kódu. Počáteční vazba snižuje počet a závažnost chyb za běhu, protože umožňuje kompilátoru hlásit chyby při kompilaci programu.  
  
> [!NOTE]
> Pozdní vazbu lze použít pouze pro přístup ke členům typu, které jsou deklarovány jako `Public` . Přístup ke členům deklarovaným jako `Friend` nebo `Protected Friend` má za následek chybu v době běhu.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Doba života objektu: Vytváření a zničení objektů](../objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
