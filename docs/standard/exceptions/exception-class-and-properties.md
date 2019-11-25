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
ms.openlocfilehash: e17fa07fe2dd19cdcd03bc923940abfef886219c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283125"
---
# <a name="exception-class-and-properties"></a>Třída a vlastnosti výjimky

Třída <xref:System.Exception> je základní třídou, ze které dědí výjimky. Například hierarchie třídy <xref:System.InvalidCastException> je následující:

<xref:System.Object>\
&nbsp;&nbsp;<xref:System.Exception>\
&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.SystemException>\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.InvalidCastException>

Třída <xref:System.Exception> má následující vlastnosti, které usnadňují porozumění výjimce.

| Název vlastnosti | Popis |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <xref:System.Collections.IDictionary>, který uchovává libovolná data v páru klíč-hodnota. |
| <xref:System.Exception.HelpLink> | Může uchovávat adresu URL (nebo název URN) souboru s nápovědu, který poskytuje rozsáhlé informace o příčině výjimky. |
| <xref:System.Exception.InnerException> | Tato vlastnost se dá použít k vytvoření a zachování řady výjimek během zpracování výjimek. Můžete ji použít k vytvoření nové výjimky, která obsahuje dříve zachycené výjimky. Původní výjimku lze zachytit druhou výjimkou ve vlastnosti <xref:System.Exception.InnerException>, což umožňuje, aby kód, který zpracovává druhou výjimku, kontroloval Další informace. Předpokládejme například, že máte metodu, která přijímá argument, který je nesprávně naformátován.  Kód se pokusí přečíst argument, ale je vyvolána výjimka. Metoda zachytí výjimku a vyvolá <xref:System.FormatException>. Aby bylo možné vylepšit schopnost volajícího určit důvod vyvolání výjimky, je někdy žádoucí, aby metoda zachytit výjimku vyvolanou pomocnou rutinou a poté vyvolat výjimku podrobnější informace o chybě, k níž došlo. Je možné vytvořit novou a smysluplnou výjimku, kde odkaz na vnitřní výjimku lze nastavit na původní výjimku. Tato smysluplná výjimka může být vyvolána volajícímu. Všimněte si, že tato funkce umožňuje vytvořit řadu propojených výjimek, které končí výjimkou, která byla vyvolána jako první. |
| <xref:System.Exception.Message> | Poskytuje podrobnosti o příčině výjimky.
| <xref:System.Exception.Source> | Získá nebo nastaví název aplikace nebo objektu, který způsobuje chybu. |
| <xref:System.Exception.StackTrace>| Obsahuje trasování zásobníku, které lze použít k určení, kde došlo k chybě. Trasování zásobníku obsahuje název zdrojového souboru a číslo řádku programu, pokud jsou k dispozici informace o ladění. |

Většina tříd, které dědí z <xref:System.Exception> neimplementuje další členy ani neposkytují další funkce. jednoduše dědí z <xref:System.Exception>. Proto nejdůležitější informace pro výjimku lze nalézt v hierarchii tříd výjimek, název výjimky a informace obsažené ve výjimce.

Doporučujeme, abyste vyvolali a zachytával pouze objekty, které jsou odvozeny z <xref:System.Exception>, ale můžete vyvolat libovolný objekt, který je odvozen od <xref:System.Object> třídy jako výjimka. Všimněte si, že ne všechny jazyky podporují vyvolávání a zachycování objektů, které nejsou odvozeny od <xref:System.Exception>.
  
## <a name="see-also"></a>Viz také:

- [Výjimky](index.md)
