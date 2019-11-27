---
title: Různé datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346333"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Různé datové typy (Visual Basic)
Visual Basic poskytuje několik datových typů, které nejsou orientované směrem k číslům nebo znakům. Místo toho pracují se specializovanými daty, jako jsou Ano/bez hodnot, hodnoty data a času a adresy objektů.  
  
 Tabulka znázorňující souběžné porovnání Visual Basic datových typů najdete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ Boolean  
 [Logický datový typ](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) je hodnota bez znaménka, která je interpretována jako buď `True`, nebo `False`. Šířka jeho dat závisí na implementaci platformy. Pokud proměnná může obsahovat pouze hodnoty se dvěma stavy, jako je true/false, Yes/No nebo on/off, deklarujte ji jako `Boolean`.  
  
## <a name="date-type"></a>Typ data  
 [Datový typ Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) je 64 hodnota, která obsahuje informace o datu a čase. Každý přírůstek představuje 100 nanosekund, jejichž uplynulý čas skončil 12:00 od 1. ledna v roce 1 v gregoriánském kalendáři. Pokud proměnná může obsahovat hodnotu data, hodnotu času nebo obojí, deklarujte ji jako `Date`.  
  
## <a name="object-type"></a>Typ objektu  
 [Datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) je 32 adresa, která odkazuje na instanci objektu v rámci aplikace nebo v jiné aplikaci. `Object` proměnná může odkazovat na libovolný objekt, který vaše aplikace rozpoznává, nebo na data libovolného datového typu. To zahrnuje *typy hodnot*, například `Integer`, `Boolean`a instance struktury a *typy odkazů*, které jsou instancemi objektů vytvořených z tříd, jako jsou `String` a <xref:System.Windows.Forms.Form>a instance polí.  
  
 Pokud proměnná ukládá ukazatel na instanci třídy, kterou neznáte v době kompilace, nebo pokud může ukazovat na data různých datových typů, deklarujte ji jako `Object`.  
  
 Výhodou `Object` datového typu je, že ho můžete použít k ukládání dat libovolného datového typu. Nevýhodou je, že se vám účtují další operace, které zabírají větší dobu spuštění a pomaleji aplikace. Použijete-li `Object` proměnnou pro typy hodnot, získáte *zabalení* a *rozbalení*. Pokud ho použijete pro typy odkazů, bude se vám účtovat *pozdní vazba*.  
  
## <a name="see-also"></a>Viz také:

- [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Číselné datové typy](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Statické a pozdní vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
