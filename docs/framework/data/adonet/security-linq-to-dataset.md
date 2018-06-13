---
title: Zabezpečení (LINQ na DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 43d529b6f74b58783cc2aaa7a81b2f75790b4e40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364958"
---
# <a name="security-linq-to-dataset"></a>Zabezpečení (LINQ na DataSet)
Toto téma popisuje problémy se zabezpečením v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Předání dotazu nedůvěryhodné součásti  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu lze formulovali v jeden bod programu a spustit v jiné. V okamžiku, kdy je formulovali dotaz můžete odkazovat dotaz libovolný element, který je zobrazen v tomto bodě, jako je například soukromé členy třídy, která volání metoda patří nebo symboly reprezentující místní proměnné nebo argumenty. V době provedení dotazu efektivně bude mít přístup k těmto členům, které byly odkazuje dotaz u formulování, i v případě, že kód volání nemá jejich přehled. Kód, který provede daný dotaz nemá libovolný účely zvýraznění v, že nemůžete vybrat, co pro přístup. Bude moct přistupovat výhradně co dotaz přistupuje ke a pouze prostřednictvím samotný dotaz.  
  
 To znamená, že pomocí předání odkazem na dotaz jinou částí kódu komponentu přijetí dotaz je se důvěryhodný s přístupem pro všechny veřejné a soukromé členy, které dotaz odkazuje na. Obecně platí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy by neměly být předány do nedůvěryhodné součásti, pokud dotaz obsahuje byla pečlivě proveden tak, aby nevystavuje informace, které by měly být udržovány privátní.  
  
## <a name="external-input"></a>Externí vstup  
 Aplikace často trvat externí vstup (uživatele nebo jiné externí agenta) a provádět akce na základě těchto informací.  U [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], aplikace může vytvořit dotaz určitým způsobem, na základě externí vstup nebo použijte externí vstup v dotazu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy přijmout všude, kde parametry, že jsou přijaty literály. Vývojáři aplikací používejte parametrizované dotazy, nikoli vložení literály z externí agenta přímo do dotazu.  
  
 Žádný vstup přímo nebo nepřímo odvozené od uživatele nebo externí agenta může mít obsah, který využívá syntaxe jazyka cíl za účelem provedení neoprávněným akcím. Tomu se říká útok prostřednictvím injektáže SQL s názvem po útoku vzor, kde je cílové jazyka Transact-SQL. Uživatelský vstup vloženy přímo do dotazu se používá k vyřadit tabulku databáze, způsobit odepření služby nebo v opačném případě změňte povaha prováděnou operaci. I když je možné v sestavení dotazu [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], se provádí prostřednictvím rozhraní API modelu objektu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy nejsou pomocí zacházení s řetězci nebo zřetězení, jak jsou v Transact-SQL a nejsou náchylné k útokům Injektáž SQL v tom smyslu, tradiční skládá.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
