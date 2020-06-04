---
title: Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397347"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Rozpoznání s pozdní vazbou; mohlo by dojít k chybám za běhu.
Objekt je přiřazen proměnné deklarované jako [datový typ objektu](../data-types/object-data-type.md).  
  
 Pokud deklarujete proměnnou jako `Object` , kompilátor musí provést *pozdní vazbu*, což způsobí dodatečné operace za běhu. Také zpřístupňuje vaši aplikaci potenciálním chybám za běhu. Například pokud přiřadíte <xref:System.Windows.Forms.Form> `Object` proměnné a potom se pokusíte o přístup k <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> vlastnosti, modul runtime vyvolá výjimku, <xref:System.MemberAccessException> protože <xref:System.Windows.Forms.Form> Třída nevystavuje `NameTable` vlastnost.  
  
 Pokud deklarujete proměnnou, která má být konkrétního typu, kompilátor může provádět *počáteční vazbu* v době kompilace. Výsledkem je vyšší výkon, řízený přístup ke členům konkrétního typu a lepší čitelnost kódu.  
  
 Ve výchozím nastavení je tato zpráva upozornění. Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42017  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud je to možné, deklarujte proměnnou, která má být specifického typu.  
  
## <a name="see-also"></a>Viz také

- [Počáteční a pozdní vazba](../../programming-guide/language-features/early-late-binding/index.md)
- [Deklarace proměnné objektu](../../programming-guide/language-features/variables/object-variable-declaration.md)
