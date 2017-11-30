---
title: "Ladění LINQ na dotazy, datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 964a4d051600621d581e05dcf6b518b2766e2750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-linq-to-dataset-queries"></a>Ladění LINQ na dotazy, datové sady
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]podporuje ladění z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kódu. Existují však určité rozdíly mezi ladění [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kódu a jiných-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] spravovaného kódu. Většina funkce ladění pracovat s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkazy, včetně krokování, nastavení zarážek a zobrazení výsledků, které jsou zobrazeny v ladicího programu. Však odložené dotazu ve má některé vedlejší účinky, které byste měli zvážit při ladění [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kód a některá omezení pomocí upravit a pokračovat. Toto téma popisuje aspekty ladění, které jsou jedinečné pro [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ve srovnání s jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] spravovaného kódu.  
  
## <a name="viewing-results"></a>Zobrazení výsledků  
 Můžete zobrazit výsledek [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkaz pomocí datatips – okno kukátka a dialogové okno QuickWatch. Pomocí okna, zdroj je možné pozastavit ukazatele na dotazu v okně zdroje a datového tipu se zobrazí. Můžete zkopírovat [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] proměnné a vložte ho do okna kukátka nebo dialogového okna QuickWatch. V [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], dotazu, nebude hodnocen při vytvoření nebo deklarovat, ale jenom v případě, že dotaz proveden. To se označuje jako *odložené spouštění*. Proměnné dotazu proto nemá hodnotu, dokud je vyhodnocena. Další informace najdete v tématu [dotazy v LINQ na DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Ladicí program se musí vyhodnotit dotazu pro zobrazení výsledků dotazu. Při zobrazení dojde k této implicitní vyhodnocení [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] výsledek dotazu v ladicím programu ale má některé důsledky, měli byste zvážit. Každého vyhodnocení dotazu trvá určitou dobu. Rozšíření uzlu výsledky trvá určitou dobu. Pro některé dotazy opakované vyhodnocení může způsobit snížení výkonu znatelné. Vyhodnocení dotazu může také způsobit vedlejší účinky, které se změní na hodnotu data a stav vašeho programu. Ne všechny dotazy mají vedlejší účinky. Pokud chcete zjistit, zda dotazu lze bezpečně vyhodnotit bez vedlejší účinky, musíte pochopit kód, který implementuje dotazu. Další informace najdete v tématu [vedlejší efekty a výrazy](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Upravit a pokračovat  
 Upravit a pokračovat nepodporuje změny [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy. Je-li přidat, odebrat nebo změnit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkaz během relace ladění, zobrazí se dialogové okno informující o změnu nepodporuje upravit a pokračovat. V tomto okamžiku můžete buď vrátit zpět změny nebo ukončit relaci ladění a restartujte novou relaci upravená kódem.  
  
 Kromě toho upravit a pokračovat nepodporuje změnu typ nebo hodnotu proměnné, která se používá v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkaz. Znovu můžete buď vrátit zpátky změny, nebo zastavte a restartujte relaci ladění.  
  
 V jazyce Visual C# v sadě Visual Studio, nemůžete použít upravit a pokračovat na žádný kód v metodě, která obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu.  
  
 V jazyce Visual Basic v sadě Visual Studio, můžete použít upravit a pokračovat na jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kód, a to i v metodu, která obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Můžete přidat nebo odebrat kód před [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] prohlášení, i když vliv budou změny mít čísla [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. V jazyce Visual Basic ladění prostředí pro jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kód zůstane stejný, jako byl před [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] byla zavedena. Nelze měnit, přidávat ani odebírat [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz, ale pokud zastavíte ladění, aby se změny projevily.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](/visualstudio/debugger/debugging-managed-code)  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
