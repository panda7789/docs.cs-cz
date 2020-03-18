---
title: Třída a vlastnosti výjimky
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
ms.openlocfilehash: df05150a5bdd5d24766be252f5cec9a436720d8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708942"
---
# <a name="exception-class-and-properties"></a>Třída a vlastnosti výjimky

Třída <xref:System.Exception> je základní třída, ze které dědí výjimky. Hierarchie <xref:System.InvalidCastException> tříd je například následující:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

Třída <xref:System.Exception> má následující vlastnosti, které pomáhají usnadnit pochopení výjimky.

| Název vlastnosti | Popis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | A <xref:System.Collections.IDictionary> který obsahuje libovolná data v párech klíč hodnota. |
| <xref:System.Exception.HelpLink> | Může obsahovat adresu URL (nebo URN) do souboru nápovědy, který poskytuje rozsáhlé informace o příčině výjimky. |
| <xref:System.Exception.InnerException> | Tuto vlastnost lze použít k vytvoření a zachování řady výjimek během zpracování výjimek. Můžete ji použít k vytvoření nové výjimky, která obsahuje dříve zachycené výjimky. Původní výjimku lze zachytit druhou výjimkou <xref:System.Exception.InnerException> ve vlastnosti, což umožňuje kód, který zpracovává druhou výjimku pro zkoumání dalších informací. Předpokládejme například, že máte metodu, která obdrží argument, který je nesprávně formátován.  Kód se pokusí přečíst argument, ale je vyvolána výjimka. Metoda zachytí výjimku a <xref:System.FormatException>vyvolá . Chcete-li zlepšit schopnost volajícího určit důvod, proč je vyvolána výjimka, je někdy žádoucí pro metodu zachytit výjimku vyvolána rutinou pomocníka a pak vyvolat výjimku, která více indikuje chybu, ke které došlo. Může být vytvořena nová a smysluplnější výjimka, kde lze na původní výjimku nastavit odkaz na vnitřní výjimku. Tato smysluplnější výjimka pak může být vyvolána volajícímu. Všimněte si, že s touto funkcí můžete vytvořit řadu propojených výjimek, které končí s výjimkou, která byla vyvolána jako první. |
| <xref:System.Exception.Message> | Obsahuje podrobnosti o příčině výjimky.
| <xref:System.Exception.Source> | Získá nebo nastaví název aplikace nebo objekt, který způsobuje chybu. |
| <xref:System.Exception.StackTrace>| Obsahuje trasování zásobníku, které lze použít k určení, kde došlo k chybě. Trasování zásobníku zahrnuje název zdrojového souboru a číslo řádku programu, pokud jsou k dispozici informace o ladění. |

Většina tříd, které <xref:System.Exception> dědí z neimplementují další členy nebo poskytují další funkce; oni prostě <xref:System.Exception>dědí od . Proto nejdůležitější informace pro výjimku lze nalézt v hierarchii tříd výjimek, název výjimky a informace obsažené v výjimce.

Doporučujeme vyvolat a zachytit pouze objekty, které jsou odvozeny z <xref:System.Exception> <xref:System.Object> aplikace , ale můžete vyvolat libovolný objekt, který je odvozen z třídy jako výjimku. Všimněte si, že ne všechny jazyky podporují <xref:System.Exception>vyvolání a zachycení objektů, které nejsou odvozeny z .
  
## <a name="see-also"></a>Viz také

- [Výjimky](index.md)
