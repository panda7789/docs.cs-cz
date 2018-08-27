---
title: Různé datové typy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 490a462859a916d21c816ff96c47d2deeb9312ee
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931135"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Různé datové typy (Visual Basic)
Visual Basic poskytuje několik typů dat, které nejsou orientovány čísel nebo znaků. Místo toho se vypořádají s specializované dat, jako Ano/ne hodnoty, hodnoty data a času a adresy objektu.  
  
 Tabulka zobrazující vedle sebe porovnání datových typů jazyka Visual Basic, naleznete v tématu [datové typy](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ Boolean  
 [Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) je hodnoty bez znaménka, je interpretován jako buď `True` nebo `False`. Šířku dat závisí na implementaci platformy. Pokud proměnná může obsahovat jenom hodnoty dvou stavů například true nebo false, Ano/Ne, nebo zapnuto/vypnuto, deklarujte ho jako `Boolean`.  
  
## <a name="date-type"></a>Date – typ  
 [Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) je 64 bitů hodnotu, která uchovává informace o datu a času. Každý přírůstek představuje 100 nanosekund uplynulý čas od počátku (12:00 AM) z 1. ledna roku 1 v gregoriánském kalendáři. Pokud proměnná může obsahovat hodnotu Datum a časové hodnoty, deklarujte ho jako `Date`.  
  
## <a name="object-type"></a>Typ objektu  
 [Datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) je 32bitová adresa, která odkazuje na instanci objektu v rámci vaší aplikace nebo v nějaké jiné aplikaci. `Object` Proměnné může odkazovat na libovolný objekt aplikace rozpozná, nebo k datům z libovolného datového typu. To zahrnuje i *typů hodnot*, jako například `Integer`, `Boolean`a struktura instance a *referenční typy*, které jsou instancemi objekty vytvořené z třídy, jako `String`a <xref:System.Windows.Forms.Form>a pole instance.  
  
 Pokud proměnná uchovává ukazatel na instanci třídy, která si nejste jisti v době kompilace, nebo pokud může odkazovat na data různých typů dat, deklarujte ho jako `Object`.  
  
 Výhodou `Object` datový typ je, že se použije k ukládání dat libovolného datového typu. Nevýhodou je, že se vám účtovat žádné další operace, které potřebují delší dobu spuštění a vaše aplikace pracovat pomaleji. Pokud používáte `Object` proměnné pro typy hodnot, se vám účtovat *zabalení* a *rozbalení*. Když ho používáte pro typy odkazů, se vám účtovat *pozdní vazby*.  
  
## <a name="see-also"></a>Viz také  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Číselné datové typy](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Statické a dynamické vazby](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
