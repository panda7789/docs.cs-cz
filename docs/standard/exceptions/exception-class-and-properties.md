---
title: "Třída a vlastnosti výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a>Třída a vlastnosti výjimky

<xref:System.Exception> Třída je základní třída, ze které dědí výjimky. Například <xref:System.InvalidCastException> hierarchie tříd je následující:

```
Object
  Exception
    SystemException
       InvalidCastException
```

<xref:System.Exception> Třída má následující vlastnosti, které vám pomohou zajistit pochopení výjimku jednodušší.

| Název vlastnosti | Popis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary> , Obsahuje libovolná data v páry klíč hodnota. |
| <xref:System.Exception.HelpLink> | Adresa URL (nebo název URN) můžete podržet souboru nápovědy, který poskytuje podrobné informace o příčině výjimky. |
| <xref:System.Exception.InnerException> | Tuto vlastnost lze použít k vytvoření a zachování řadu výjimky během zpracování výjimek. Můžete ho vytvořit novou výjimku, která obsahuje dříve zachycení výjimky. Původní výjimka se dají zachytit druhou výjimkou v <xref:System.Exception.InnerException> vlastnosti, což umožňuje kód, který zpracovává druhou výjimku zjistit další informace. Předpokládejme například, že máte metodu, která přijímá argument, který je v nesprávném formátu.  Kód se pokusí načíst argument, ale je vyvolána výjimka. Metoda zachytí výjimky a vyvolá výjimku <xref:System.FormatException>. Pokud chcete zlepšit volajícího schopnosti určit důvod, proč je vyvolána výjimka, je někdy žádoucí, aby metoda catch výjimka vyvolaná objektem pomocnou rutinou a poté vyvolat výjimku více popisuje chybu, která proběhla. Mohou být vytvořeny nové a smysluplnější výjimky, které lze nastavit odkaz na informacích o vnitřní výjimce původní výjimku. Tato smysluplnější výjimka může být vyvolána pak volajícímu. Všimněte si, že pomocí této funkce můžete vytvořit řadu propojených výjimek, který končí výjimku, která byla vyvolána jako první. |
| <xref:System.Exception.Message> | Obsahuje podrobné informace o příčině výjimky.
| <xref:System.Exception.Source> | Získá nebo nastaví název aplikace nebo objekt, který způsobuje chybu. |
| <xref:System.Exception.StackTrace>| Obsahuje trasování zásobníku, který slouží k určení, kde došlo k chybě. Trasování zásobníku zahrnuje zdrojový soubor název a číslo řádku, pokud ladicí informace je k dispozici. |

Většina tříd, které dědí od <xref:System.Exception> neimplementuje další členy nebo dodatečných funkcí; jednoduše dědí z <xref:System.Exception>. Proto nejdůležitější informace o výjimce naleznete v hierarchii třídy výjimek, název výjimky a informace obsažené v výjimce.

Doporučujeme, abyste throw a catch pouze objekty, které jsou odvozeny od <xref:System.Exception>, ale můžete vyvolat libovolný objekt, který je odvozen od <xref:System.Object> třída jako výjimku. Všimněte si, že ne všechny jazyky podporují vyvolávání a zachycování objekty, které není odvozena od <xref:System.Exception>.
  
## <a name="see-also"></a>Viz také  
[Výjimky](index.md)
