---
title: Typové datové sady
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 33876cb9f614a93cab2fa3fd9d056f94dd1e9038
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203162"
---
# <a name="typed-datasets"></a>Typové datové sady
Společně s přístupem s pozdní vazbou k hodnotám prostřednictvím slabých typových proměnných <xref:System.Data.DataSet> poskytuje přístup k datům prostřednictvím silného typu metafora. Tabulky a sloupce, které jsou součástí **datové sady** , mohou být k dispozici pomocí uživatelsky přívětivých názvů a proměnných se silným typem.  
  
 Typová **datová sada** je třída, která je odvozena z **datové sady**. V takovém případě dědí všechny metody, události a vlastnosti **datové sady**. Kromě toho typová **datová sada** poskytuje metody, události a vlastnosti silného typu. To znamená, že můžete získat přístup k tabulkám a sloupcům podle názvu namísto použití metod založených na kolekcích. Kromě zlepšení čitelnosti kódu umožňuje typová **datová sada** také editoru kódu sady Visual Studio .NET automatické dokončování řádků při psaní.  
  
 **Datová sada** silného typu navíc poskytuje přístup k hodnotám jako správný typ v době kompilace. V případě silně typované **datové sady**jsou zachyceny chyby neshody typů, pokud je kód zkompilován, nikoli za běhu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování datových sad se silnými typy](generating-strongly-typed-datasets.md)  
 Popisuje, jak vytvořit a použít typovou datovou **sadu**se silnými typy.  
  
 [Zadávání poznámek k typovým datovým sadám](annotating-typed-datasets.md)  
 Popisuje, jak opatřit poznámkami schéma XML schématu definice jazyka (XSD) používané k vygenerování **datové sady**se silnými typy , aby byly uživatelsky přívětivé názvy přizpůsobitelné bez změny podkladového schématu.  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
