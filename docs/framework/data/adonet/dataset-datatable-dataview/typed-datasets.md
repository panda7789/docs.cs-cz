---
title: Typové datové sady
ms.date: 03/30/2017
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
ms.openlocfilehash: 7c8111e0e62a57b6745a5ea0387fc65a05839df8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785836"
---
# <a name="typed-datasets"></a>Typové datové sady
Společně s přístupem s pozdní vazbou k hodnotám prostřednictvím slabých typových proměnných <xref:System.Data.DataSet> poskytuje přístup k datům prostřednictvím silného typu metafora. Tabulky a sloupce, které jsou součástí **datové sady** , mohou být k dispozici pomocí uživatelsky přívětivých názvů a proměnných se silným typem.  
  
 Typová **datová sada** je třída, která je odvozena z **datové sady**. V takovém případě dědí všechny metody, události a vlastnosti **datové sady**. Kromě toho typová **datová sada** poskytuje metody, události a vlastnosti silného typu. To znamená, že můžete získat přístup k tabulkám a sloupcům podle názvu namísto použití metod založených na kolekcích. Kromě zlepšení čitelnosti kódu umožňuje typová **datová sada** také editoru kódu sady Visual Studio .NET automatické dokončování řádků při psaní.  
  
 **Datová sada** silného typu navíc poskytuje přístup k hodnotám jako správný typ v době kompilace. V případě silně typované **datové sady**jsou zachyceny chyby neshody typů, pokud je kód zkompilován, nikoli za běhu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování datových sad se silnými typy](generating-strongly-typed-datasets.md)  
 Popisuje, jak vytvořit a použít typovou **datovou sadu**se silnými typy.  
  
 [Zadávání poznámek k typovým datovým sadám](annotating-typed-datasets.md)  
 Popisuje, jak opatřit poznámkami schéma XML schématu definice jazyka (XSD) používané k vygenerování **datové sady**se silnými typy , aby byly uživatelsky přívětivé názvy přizpůsobitelné bez změny podkladového schématu.  
  
## <a name="see-also"></a>Viz také:

- [Datové sady, datové tabulky a datová zobrazení](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
