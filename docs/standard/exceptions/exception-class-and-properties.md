---
title: Třída a vlastnosti výjimky
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 283b3b1aa0d56b50b6f9e67b66de3e0b68ae2331
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036343"
---
# <a name="exception-class-and-properties"></a>Třída a vlastnosti výjimky

<xref:System.Exception> Třída je základní třída, ze kterého dědí výjimky. Například <xref:System.InvalidCastException> hierarchie tříd je takto:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Třída má následující vlastnosti, které usnadňují porozumění výjimku jednodušší.

| Název vlastnosti | Popis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> Libovolná data, která obsahuje v párech klíč hodnota. |
| <xref:System.Exception.HelpLink> | Adresa URL (nebo URN) může obsahovat soubor nápovědy, která poskytuje podrobné informace o příčině výjimky. |
| <xref:System.Exception.InnerException> | Tato vlastnost slouží k vytvoření a zachovat řadu výjimek během zpracování výjimek. Můžete ho vytvořit novou výjimku, která obsahuje dříve zachycené výjimky. Původní výjimku můžete zaznamenat druhou výjimkou v <xref:System.Exception.InnerException> vlastnosti, což umožňuje kód, který zpracovává druhou výjimkou zjistit další informace. Předpokládejme například, že měl odpovídající metodu, která přijímá argument, který je v nesprávném formátu.  Kód se pokusí načíst argument, ale dojde k výjimce. Metoda zachytí výjimku a vyvolá výjimku <xref:System.FormatException>. Pokud chcete zlepšit volajícího schopnost určit důvod, proč je vyvolána výjimka, je někdy žádoucí, aby metoda zachytit výjimku vyvolanou pomocná rutina a poté vyvolají výjimku více naznačuje, že došlo k chybě. Nelze vytvořit nové a lépe vystihuje výjimky, kde lze nastavit odkaz na vnitřní výjimku v původní výjimky. Toto lépe vystihuje výjimky mohou být vyvolány pak volajícímu. Všimněte si, že tuto funkci, můžete vytvořit řadu propojené výjimek, který končí výjimku, která byla vyvolána jako první. |
| <xref:System.Exception.Message> | Obsahuje podrobné informace o příčině výjimky.
| <xref:System.Exception.Source> | Získá nebo nastaví název aplikace nebo objekt, který způsobuje chybu. |
| <xref:System.Exception.StackTrace>| Obsahuje trasování zásobníku, který slouží k určení, kde došlo k chybě. Trasování zásobníku zahrnuje zdrojový soubor název a číslo řádku, pokud informace o ladění je k dispozici. |

Většina tříd, které dědí <xref:System.Exception> implementovat další členy nebo poskytnutí dalších funkcí; jednoduše dědí z <xref:System.Exception>. Proto nejdůležitější informace o výjimce najdete v hierarchii tříd výjimek, název výjimky a informace obsažené ve výjimce.

Doporučujeme, abyste throw a catch pouze objekty, které jsou odvozeny z <xref:System.Exception>, ale může vyvolat libovolný objekt, který je odvozen od <xref:System.Object> třídu jako výjimku. Všimněte si, že nepodporují všechny jazyky vyvolávání a zachycování objekty, které nejsou odvozeny z <xref:System.Exception>.
  
## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
