---
title: Zabezpečení (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: d6f00fccb0ea2f49c19b640e31d96e575c0d48b9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782792"
---
# <a name="security-linq-to-dataset"></a>Zabezpečení (LINQ to DataSet)
Toto téma popisuje problémy se zabezpečením v LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Předání dotazu do nedůvěryhodné součásti  
 Dotaz LINQ to DataSet lze formulovat v jednom místě programu a provést v jiném. V místě, kde je vytvořen dotaz, dotaz může odkazovat na libovolný prvek, který je viditelný v tomto okamžiku, například soukromé členy třídy, do které volající metoda patří, nebo symboly představující místní proměnné/argumenty. V době spuštění bude dotaz efektivně mít přístup k těmto členům, na které byl odkaz odkazován v rámci formulace, i když volající kód nemá v nich přehled. Kód, který spustí dotaz, nemá žádnou přidanou viditelnost, v takovém případě nemůže zvolit, co má být přístupné. Bude mít přístup k striktně, k čemu dotaz přistupuje, a jenom prostřednictvím samotného dotazu.  
  
 To znamená, že předáním odkazu na dotaz do jiné části kódu, že komponenta, která přijímá dotaz, je důvěryhodná a přístup ke všem veřejným a soukromým členům, na které dotaz odkazuje. Obecně platí, že LINQ to DataSet dotazy by neměly být předány nedůvěryhodným součástem, pokud dotaz nebyl pečlivě vytvořen tak, aby nezveřejnil informace, které by měly být uchovány jako soukromé.  
  
## <a name="external-input"></a>Externí vstup  
 Aplikace často přijímají externí vstup (od uživatele nebo jiného externího agenta) a provádějí akce založené na tomto vstupu.  V případě LINQ to DataSet může aplikace vytvořit dotaz určitým způsobem na základě externího vstupu nebo použít externí vstup v dotazu. LINQ to DataSet dotazy přijímají parametry všude, kde jsou povoleny literály. Vývojáři aplikací by měli použít parametrizované dotazy místo vložení literálů z externího agenta přímo do dotazu.  
  
 Jakýkoli vstup přímo nebo nepřímo odvozený od uživatele nebo externího agenta může mít obsah, který využívá syntaxi cílového jazyka, aby mohl provádět neoprávněné akce. Tato funkce se označuje jako útok injektáže SQL pojmenovaný po způsobu útoku, kde cílový jazyk je Transact-SQL. Uživatelský vstup vložený přímo do dotazu slouží k vyřazení tabulky databáze, k odmítnutí služby nebo jiné změně povahy prováděné operace. I když je v LINQ to DataSet možné kompozice dotazů, provádí se prostřednictvím rozhraní API objektového modelu. LINQ to DataSet dotazy nejsou tvořeny pomocí manipulace s řetězci nebo zřetězení, protože jsou v jazyce Transact-SQL a nejsou náchylné k útokům prostřednictvím injektáže SQL v tradičním smyslu.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide-linq-to-dataset.md)
