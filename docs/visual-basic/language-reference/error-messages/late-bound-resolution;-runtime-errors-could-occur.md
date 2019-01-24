---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 9caf02907e4b6de4c2bd8de778d4ad7a9320a82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690576"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
Objekt je přiřazen proměnné deklarované jako [datový typ objektu](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Pokud deklarujete proměnnou pro tu `Object`, musíte provést kompilátor *pozdní vazby*, což způsobí, že další operace v době běhu. Také poskytuje aplikaci potenciální běhové chyby. Například, pokud přiřadíte <xref:System.Windows.Forms.Form> k `Object` proměnnou a pak zkuste přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnost, modul runtime vyvolá <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> třídy nevystavuje `NameTable` vlastnost.  
  
 Pokud deklarujete proměnnou deklarovanou určitého typu, kompilátor může provádět *časné vazby* v době kompilace. Výsledkem je vylepšení výkonu, řízený přístup k členům konkrétního typu a lepší čitelnost vašeho kódu.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42017  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud je to možné deklarujte proměnnou deklarovanou určitého typu.  
  
## <a name="see-also"></a>Viz také:
- [Statické a dynamické vazby](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [Deklarace objektové proměnné](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
