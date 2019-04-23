---
title: Zabezpečení (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: aa281cb4d6019ca2df85137eb505724e55b8060a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087329"
---
# <a name="security-linq-to-dataset"></a>Zabezpečení (LINQ to DataSet)
Toto téma popisuje problémy se zabezpečením v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Předávání nedůvěryhodnou součást dotazu  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu lze formulovat v jeden bod programu a spustit v jiné. V okamžiku, kdy je formulovali dotaz můžete dotaz odkazují na libovolný element, který je viditelný v tomto okamžiku, jako je například soukromým členům třídy, které patří volání metody nebo symboly reprezentující místní proměnné a argumenty. V době provádění dotazu efektivně bude mít přístup k těmto členům, které bylo odkazováno podle dotazu ve složení, i v případě, že volající kód nemá dohled nad nich. Kód, který provede daný dotaz nemá libovolného přidaného viditelnost, v tom, že nejde zvolit, jak získat přístup. Budete moct přistupovat výhradně co dotaz přistupuje ke a pouze prostřednictvím samotný dotaz.  
  
 Z toho vyplývá, že tím, že předáte odkaz na dotaz na jinou část kódu komponenty příjem dotaz je důvěryhodný s přístupem pro všechny veřejné a soukromé členy, které dotaz odkazuje. Obecně platí [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazů by neměl být předán nedůvěryhodné komponent, pokud dotaz byl pečlivě vytvořen tak, aby nezpřístupňuje informace, které by měly být neustále privátní.  
  
## <a name="external-input"></a>Externí vstup  
 Aplikace často trvat, než externí vstup (uživatele nebo jiné externí agenta) a provádět akce na základě těchto informací.  V případě třídy [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], aplikace může vytvořit dotaz určitým způsobem, na základě externí vstup, nebo použijte externí vstup v dotazu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy přijímají parametry všude, že se přijímají literály. Vývojáři aplikací používejte parametrizované dotazy, nikoli vloženého literály z externí agenta přímo do dotazu.  
  
 Všechny vstupní přímo nebo nepřímo odvozený od uživatele nebo externí agenta může být obsah, který využívá syntaxe cílový jazyk, aby bylo možné provést neoprávněným akcím. To se označuje jako útok prostřednictvím injektáže SQL, pojmenované po vzorce útoku, ve kterém je cílový jazyk Transact-SQL. Uživatelský vstup vloží přímo do dotazu se používá k vyřadit tabulku databáze, způsobit odepření služby nebo jinak změnit druh operace právě probíhá. I když sestavení dotazu je možné v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], se provádí prostřednictvím rozhraní API objektu modelu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy se skládá pomocí zacházení s řetězci nebo zřetězení, jako jsou v jazyce Transact-SQL a nejsou náchylný na útoky prostřednictvím injektáže SQL v tradičním smyslu.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
