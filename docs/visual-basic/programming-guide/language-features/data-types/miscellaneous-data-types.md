---
title: Různé datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 0a08c0e7087c3efb0e5ffce51182defae45629ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393750"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Různé datové typy (Visual Basic)
Visual Basic poskytuje několik datových typů, které nejsou orientované směrem k číslům nebo znakům. Místo toho pracují se specializovanými daty, jako jsou Ano/bez hodnot, hodnoty data a času a adresy objektů.  
  
 Tabulka znázorňující souběžné porovnání Visual Basic datových typů najdete v tématu [datové typy](../../../language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ Boolean  
 [Logický datový typ](../../../language-reference/data-types/boolean-data-type.md) je hodnota bez znaménka, která je interpretována `True` buď `False` nebo. Šířka jeho dat závisí na implementaci platformy. Pokud proměnná může obsahovat pouze hodnoty se dvěma stavy, jako je true/false, ano/ne nebo zapnuto nebo vypnuto, deklarujete je jako `Boolean` .  
  
## <a name="date-type"></a>Typ data  
 [Datový typ Date](../../../language-reference/data-types/date-data-type.md) je 64 hodnota, která obsahuje informace o datu a čase. Každý přírůstek představuje 100 nanosekund, jejichž uplynulý čas skončil 12:00 od 1. ledna v roce 1 v gregoriánském kalendáři. Pokud proměnná může obsahovat hodnotu data, hodnotu času nebo obojí, deklarujte ji jako `Date` .  
  
## <a name="object-type"></a>Typ objektu  
 [Datový typ objektu](../../../language-reference/data-types/object-data-type.md) je 32 adresa, která odkazuje na instanci objektu v rámci aplikace nebo v jiné aplikaci. `Object`Proměnná může odkazovat na libovolný objekt, který vaše aplikace rozpoznává, nebo na data libovolného datového typu. To zahrnuje *typy hodnot*, jako jsou `Integer` , `Boolean` a instance struktury a *typy odkazů*, což jsou instance objektů vytvořených z tříd, jako jsou `String` a a <xref:System.Windows.Forms.Form> instance polí.  
  
 Pokud proměnná ukládá ukazatel na instanci třídy, kterou neznáte v době kompilace, nebo pokud může ukazovat na data různých datových typů, deklarujte ji jako `Object` .  
  
 Výhodou `Object` datového typu je, že ho můžete použít k ukládání dat libovolného datového typu. Nevýhodou je, že se vám účtují další operace, které zabírají větší dobu spuštění a pomaleji aplikace. Použijete-li `Object` proměnnou pro typ hodnoty, získáte *zabalení* a *rozbalení*. Pokud ho použijete pro typy odkazů, bude se vám účtovat *pozdní vazba*.  
  
## <a name="see-also"></a>Viz také

- [Znaky typu](type-characters.md)
- [Základní datové typy](elementary-data-types.md)
- [Číselné datové typy](numeric-data-types.md)
- [Znakové datové typy](character-data-types.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
- [Počáteční a pozdní vazba](../early-late-binding/index.md)
