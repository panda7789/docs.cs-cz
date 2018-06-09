---
title: Úkoly strojového učení
description: Prozkoumejte různé strojového učení úlohy v ML.NET podporovány.
ms.date: 06/04/2018
author: aditidugar
ms.author: johalex
ms.openlocfilehash: 22249ac2d275a4168dbd8b03b90d9698fe90f2d1
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "35017274"
---
# <a name="machine-learning-tasks"></a>Úkoly strojového učení

Při sestavování strojového učení modelu, musíte nejprve definovat, co jsou doufá k dosažení s daty. Po můžete si vybrat správné strojového učení úloh pro vaši situaci. Následující seznam popisuje různé strojového učení úlohy, které můžete vybrat z a některé běžné případy použití. 

> [!NOTE]
> ML.NET je aktuálně ve verzi Preview. Ne všechny úkoly strojového učení jsou aktuálně podporovány. Chcete-li odeslat žádost o konkrétní úlohu, otevřete problém v [úložiště dotnet/machinelearning](https://github.com/dotnet/machinelearning/issues).

> [!NOTE]
> ML.NET v současné době nepodporuje úkoly strojového učení s obrázky. Podpora budou přidané do budoucích verzí. 

## <a name="binary-classification"></a>binární klasifikace

A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která je použít k předpovědi, které instance dat patří do dvou tříd (kategorie). Vstup klasifikační algoritmus je sada s popiskem příklady, kde každý popisek je celé číslo 0 nebo 1. Výstup binární klasifikace algoritmem je třídění, který můžete použít k předpovědi třídu nové instance služby bez popisku. Příklady scénářů binární klasifikace:

* [Principy postojích Twitter komentářů](../tutorials/sentiment-analysis.md) jako "pozitivní" nebo "negativní".
* Diagnostikování zda pacienta má určitá nákazy, nebo ne.
* Rozhodování označit e-mailu jako "spamu", nebo ne.

## <a name="multi-class-classification"></a>Klasifikace více – třída

A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která se používá k předvídání – třída (kategorie) instance data. Vstup klasifikační algoritmus je sada s popiskem příklady. Každý popisek je celé číslo mezi 0 a k-1, kde k je počet tříd. Výstup klasifikační algoritmus je třídění, který můžete použít k předpovědi třídu nové instance služby bez popisku. Příklady scénářů více třída klasifikace:

* Zjišťuje se druh PSA jako "Siberian Husky", "Zlatá načítací modul pro", "Co", atd.
* Principy film zkontroluje jako "pozitivní", "neutrální" nebo "negativní".
* Kategorizaci hotelů zkontroluje jako "místo", "cena", "čistoty", atd.

## <a name="regression"></a>Regrese

A [počítač učení se supervizí](glossary.md#supervised-machine-learning) úlohu, která se používá k předvídání hodnotu popisku ze sady souvisejících funkcí. Popisek může být jakékoli skutečné hodnoty a nikoli z konečného počtu permutací nastavena hodnot jako klasifikace úlohy. Jsou nastaveny regresní model algoritmy závislost popisek na jeho souvisejících funkcí k určení, jak se změní štítek jako hodnoty funkcí. Vstup regresní algoritmus je sada příklady s popisky známé hodnoty. Výstup regresní algoritmus je funkce, který můžete použít k předpovědi hodnotu popisku pro všechny nové sady vstupní funkcí. Příklady scénářů regrese:

* Předpověď ceny Domů na základě atributů úklidové jako Počet ložnic, umístění a velikost.
* Předpovídat budoucí uložených ceny na základě historických dat a aktuální vývoj trhu.
* Předpověď prodeje podle inzerování rozpočty produktu.

> [!NOTE]
> V současné době ML.NET je stále vytváření podporu pro regresní úlohy, které zahrnují časové řady.

## <a name="clustering"></a>Clustering

[Supervize počítač](glossary.md#unsupervised-machine-learning) úlohu, která se používá k skupiny instance dat do clusterů obsahující podobné charakteristiky. Clustering lze také identifikovat vztahy v datovou sadu, která nemusí být logicky podle procházení nebo jednoduše pozorování. Vstupy a výstupy clustering algoritmu závisí na zvolené metody. Může trvat distribuce, těžiště, připojení nebo na základě hustotu přístup. ML.NET aktuálně podporuje použití clusteringu K-Means o přístupu na základě těžiště. Příklady scénáře clusteringu:

* Principy segmenty hotelů hostů na základě zvyklosti a charakteristika hotelů volby.
* Identifikace segmenty zákazníků a demografie usnadňující tvorbu cílové reklamní kampaně.
* Kategorizaci inventáře podle výrobní metriky.

## <a name="anomaly-detection-coming-soon"></a>Detekce anomálií (*připravuje*)

## <a name="ranking-coming-soon"></a>Řazení (*připravuje*)

## <a name="recommendation-coming-soon"></a>Doporučení (*připravuje*)

