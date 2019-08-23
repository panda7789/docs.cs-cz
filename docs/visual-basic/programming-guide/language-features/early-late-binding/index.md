---
title: Statické a pozdní vazby (Visual Basic)
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
ms.openlocfilehash: d05322ba831aac6173ac9d7fa7f369a208b676d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965380"
---
# <a name="early-and-late-binding-visual-basic"></a>Statické a pozdní vazby (Visual Basic)
Kompilátor Visual Basic provádí proces, který se `binding` volá, když se objekt přiřadí proměnné objektu. Objekt je *časné vazby* , je-li přiřazen k proměnné deklarované jako pro určitý typ objektu. Předčasný vázané objekty umožňují kompilátoru přidělit paměť a provádět další optimalizace před spuštěním aplikace. Například následující fragment kódu deklaruje proměnnou, která bude typu <xref:System.IO.FileStream>:  
  
 [!code-vb[VbVbalrOOP#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#90)]  
  
 Vzhledem <xref:System.IO.FileStream> k tomu, že se jedná o konkrétní typ objektu `FS` , je instance přiřazená k předčasnému vázání.  
  
 Naopak objekt je *pozdní vazba* , pokud je přiřazena proměnné deklarované jako typ `Object`. Objekty tohoto typu můžou uchovávat odkazy na libovolný objekt, ale nemají spoustu výhod objektů s časnou vazbou. Například následující fragment kódu deklaruje proměnnou objektu pro uchování objektu vráceného `CreateObject` funkcí:  
  
 [!code-vb[VbVbalrOOP#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/LateBinding.vb#91)]  
  
## <a name="advantages-of-early-binding"></a>Výhody prvotní vazby  
 Pokud je to možné, měli byste použít objekty s časnou vazbou, protože umožňují kompilátoru provádět důležité optimalizace, které přinesou efektivnější aplikace. Objekty s časnou vazbou jsou výrazně rychlejší než objekty s pozdní vazbou a usnadňují čtení a údržbu kódu tím, že přesně udávají, jaký typ objektů se používá. Další výhodou pro předčasné vázání je to, že umožňuje použití užitečných funkcí, jako je automatické dokončování kódu a dynamické pomoci, protože integrované vývojové prostředí (IDE) sady Visual Studio dokáže přesně určit, se kterým typem objektu pracujete při úpravách znakovou. Počáteční vazba snižuje počet a závažnost chyb za běhu, protože umožňuje kompilátoru hlásit chyby při kompilaci programu.  
  
> [!NOTE]
> Pozdní vazbu lze použít pouze pro přístup ke členům typu, které jsou deklarovány jako `Public`. Přístup ke členům deklarovaným `Protected Friend` jako `Friend` nebo má za následek chybu v době běhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>
- [Doba života objektu: Vytváření a zničení objektů](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
