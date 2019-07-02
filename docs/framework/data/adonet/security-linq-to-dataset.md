---
title: Zabezpečení (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504253"
---
# <a name="security-linq-to-dataset"></a>Zabezpečení (LINQ to DataSet)
Toto téma popisuje problémy se zabezpečením v technologii LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Předávání nedůvěryhodnou součást dotazu  
 LINQ to DataSet dotazu lze formulovat v jeden bod programu a spustit v jiné. V okamžiku, kdy je formulovali dotaz můžete dotaz odkazují na libovolný element, který je viditelný v tomto okamžiku, jako je například soukromým členům třídy, které patří volání metody nebo symboly reprezentující místní proměnné a argumenty. V době provádění dotazu efektivně bude mít přístup k těmto členům, které bylo odkazováno podle dotazu ve složení, i v případě, že volající kód nemá dohled nad nich. Kód, který provede daný dotaz nemá libovolného přidaného viditelnost, v tom, že nejde zvolit, jak získat přístup. Budete moct přistupovat výhradně co dotaz přistupuje ke a pouze prostřednictvím samotný dotaz.  
  
 Z toho vyplývá, že tím, že předáte odkaz na dotaz na jinou část kódu komponenty příjem dotaz je důvěryhodný s přístupem pro všechny veřejné a soukromé členy, které dotaz odkazuje. Obecně platí, LINQ to DataSet dotazů by neměl být předán nedůvěryhodné komponent, pokud dotaz byl pečlivě vytvořen tak, aby nezpřístupňuje informace, které by měly být neustále privátní.  
  
## <a name="external-input"></a>Externí vstup  
 Aplikace často trvat, než externí vstup (uživatele nebo jiné externí agenta) a provádět akce na základě těchto informací.  Aplikace může v případě LINQ k datové sadě, sestavte dotaz určitým způsobem, na základě externí vstup, nebo použijte externí vstup v dotazu. Technologie LINQ to DataSet dotazy přijímají parametry všude, že se přijímají literály. Vývojáři aplikací používejte parametrizované dotazy, nikoli vloženého literály z externí agenta přímo do dotazu.  
  
 Všechny vstupní přímo nebo nepřímo odvozený od uživatele nebo externí agenta může být obsah, který využívá syntaxe cílový jazyk, aby bylo možné provést neoprávněným akcím. To se označuje jako útok prostřednictvím injektáže SQL, pojmenované po vzorce útoku, ve kterém je cílový jazyk Transact-SQL. Uživatelský vstup vloží přímo do dotazu se používá k vyřadit tabulku databáze, způsobit odepření služby nebo jinak změnit druh operace právě probíhá. I když sestavení dotazu je možné v technologii LINQ to DataSet, se provádí prostřednictvím rozhraní API objektu modelu. Technologie LINQ to DataSet dotazy nejsou skládá pomocí zacházení s řetězci nebo zřetězení, jako jsou v jazyce Transact-SQL a nejsou náchylný na útoky prostřednictvím injektáže SQL v tradičním smyslu.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
