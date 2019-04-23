---
title: Ladění dotazů v LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 0e015cc6042a21bf6d35915c3e19bfeb9b0dbb2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133326"
---
# <a name="debugging-linq-to-dataset-queries"></a>Ladění dotazů v LINQ to DataSet

Visual Studio podporuje ladění [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kódu. Existují však určité rozdíly mezi ladění [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kódu a jiné-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] spravovaného kódu. Většina funkcí ladění pracuje s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkazy, včetně posílení, nastavení zarážek a zobrazení výsledků, které jsou zobrazeny v oknech ladicího programu. Však odložené dotazu provádění ve službě má některé vedlejší účinky, které byste měli zvážit během ladění [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kódu a narazíte na určitá omezení pomocí funkce upravit a pokračovat. Toto téma popisuje aspekty ladění, které jsou jedinečné pro [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ve srovnání s jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] spravovaného kódu.  
  
## <a name="viewing-results"></a>Zobrazení výsledků  
 Můžete zobrazit výsledek [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkaz pomocí datových tipů, okna kukátka a dialogového okna rychlého kukátka. Pomocí okna zdroje můžete pozastavíte ukazatel myši na dotazu v okně zdroje a zobrazí se datatip. Můžete zkopírovat [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] proměnné a vložte ho do okna kukátka nebo dialogového okna rychlého kukátka. V [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], dotaz není vyhodnocen při vytváření nebo deklaraci, ale pouze při spuštění dotazu. Tento postup se nazývá *odložené provedení*. Proměnné dotazu, proto nemá hodnotu, dokud není vyhodnocen. Další informace najdete v tématu [dotazy v LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Ladicí program se musí vyhodnotit dotazu pro zobrazení výsledků dotazu. Toto implicitní hodnocení vyvolá se při zobrazení [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] výsledek dotazu v ladicím programu který má některé efekty, měli byste zvážit. Každé vyhodnocení dotazu trvá určitou dobu. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů opakované hodnocení může způsobit znatelné penalizace. Vyhodnocení dotazu může také způsobit vedlejší účinky, které znamenají změnu hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Pokud chcete zjistit, zda dotaz může být bezpečně zhodnocen bez vedlejších účinků, je třeba pochopit kód, který implementuje dotaz. Další informace najdete v tématu [vedlejší efekty a výrazy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Upravit a pokračovat  
 Upravit a pokračovat nepodporuje změny [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazy. Je-li přidat, odebrat nebo změnit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkaz během relace ladění, zobrazí se dialogové okno s oznámením, tato změna není podporována možností upravit a pokračovat. V tomto okamžiku můžete buď vrátit zpět změny nebo zastavit ladicí relaci a znovu spustit novou relaci s upraveným kódem.  
  
 Kromě toho upravit a pokračovat nepodporuje změnu typu ani hodnoty proměnné, který se používá v [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] příkazu. Znovu můžete buď vrátit zpět změny nebo zastavte a restartujte relaci ladění.  
  
 V jazyce Visual C# v sadě Visual Studio nelze použít funkce upravit a pokračovat na žádný kód v metodě, která obsahuje [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu.  
  
 V jazyce Visual Basic v sadě Visual Studio, můžete použít funkce upravit a pokračovat na jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kód v metodě, která obsahuje i [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. Můžete přidat nebo odebrat kód před [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] prohlášení, i v případě, že změny ovlivní počet řádků [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. V jazyce Visual Basic prostředí ladění pro jinou hodnotu než[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kód zůstane stejné, jako byl před [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] byla zavedena. Nejde změnit, přidat nebo odebrat [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazování, ale pokud zastavíte ladění, aby se změny projevily.  
  
## <a name="see-also"></a>Viz také:

- [Ladění spravovaného kódu](/visualstudio/debugger/debugging-managed-code)
- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
