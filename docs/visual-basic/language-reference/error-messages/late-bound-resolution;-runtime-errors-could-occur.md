---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: af027b7752fdf13f1540010a8ddb681182c1b23c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
Objekt je přiřazený k proměnné deklarované jako [Object – datový typ](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Když deklarovat proměnnou jako `Object`, musíte provést kompilátor *pozdní vazby*, což způsobí, že další operace v době běhu. Taky zpřístupňuje potenciální chyby při spuštění aplikace. Například, pokud přiřadíte <xref:System.Windows.Forms.Form> k `Object` proměnnou a pak zkuste přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnost, modul runtime vyvolá <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> třída nevystavuje `NameTable` vlastnost.  
  
 Pokud je deklarovat proměnnou být určitého typu, můžete provést kompilátor *časné vazby* v době kompilace. Výsledkem je lepší výkon, řízený přístup členů specifický typ a lepší čitelnost kódu.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42017  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné deklarujte proměnnou být určitého typu.  
  
## <a name="see-also"></a>Viz také  
 [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [Deklarace objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
