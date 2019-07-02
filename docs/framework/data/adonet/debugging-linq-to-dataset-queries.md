---
title: Ladění dotazů v LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 38eda9f352c4a8d8590e5e57b48c694eadd0397b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503985"
---
# <a name="debugging-linq-to-dataset-queries"></a>Ladění dotazů v LINQ to DataSet

Visual Studio podporuje ladění LINQ k datové sadě kódu. Existují však určité rozdíly mezi ladění LINQ na DataSet kódu a jiných – LINQ to DataSet spravované kód. Většina funkcí ladění pracuje s dotazy LINQ na datovou sadu příkazů, včetně posílení, nastavení zarážek a zobrazení výsledků, které jsou zobrazeny v oknech ladicího programu. Ale provádění odložených dotazů v má některé vedlejší účinky, které byste měli zvážit během ladění LINQ k datové sadě kódu a narazíte na určitá omezení pomocí funkce upravit a pokračovat. Toto téma popisuje aspekty ladění, které jsou jedinečné pro LINQ to DataSet v porovnání s mimo LINQ to DataSet spravované kódu.  
  
## <a name="viewing-results"></a>Zobrazení výsledků  
 Výsledek LINQ to DataSet příkazu můžete zobrazit pomocí datových tipů, okna kukátka a dialogového okna rychlého kukátka. Pomocí okna zdroje můžete pozastavíte ukazatel myši na dotazu v okně zdroje a zobrazí se datatip. Můžete zkopírovat LINQ k datové sadě proměnné a vložte ho do okna kukátka nebo dialogového okna rychlého kukátka. V technologii LINQ to DataSet dotaz není vyhodnocen při vytváření nebo deklaraci, ale pouze při spuštění dotazu. Tento postup se nazývá *odložené provedení*. Proměnné dotazu, proto nemá hodnotu, dokud není vyhodnocen. Další informace najdete v tématu [dotazy v LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Ladicí program se musí vyhodnotit dotazu pro zobrazení výsledků dotazu. Toto implicitní hodnocení vyvolá se při zobrazení na datovou sadu výsledků dotazu LINQ v ladicím programu a má některé efekty, které byste měli zvážit. Každé vyhodnocení dotazu trvá určitou dobu. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů opakované hodnocení může způsobit znatelné penalizace. Vyhodnocení dotazu může také způsobit vedlejší účinky, které znamenají změnu hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Pokud chcete zjistit, zda dotaz může být bezpečně zhodnocen bez vedlejších účinků, je třeba pochopit kód, který implementuje dotaz. Další informace najdete v tématu [vedlejší efekty a výrazy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Upravit a pokračovat  
 Upravit a pokračovat nepodporuje změny do datové sady dotazů LINQ. Je-li přidat, odebrat nebo změnit LINQ na DataSet příkaz během relace ladění, zobrazí se dialogové okno s oznámením, že tato změna není podporována možností upravit a pokračovat. V tomto okamžiku můžete buď vrátit zpět změny nebo zastavit ladicí relaci a znovu spustit novou relaci s upraveným kódem.  
  
 Kromě toho upravit a pokračovat nepodporuje změnu typu ani hodnoty proměnné, který se používá v technologii LINQ to DataSet příkazu. Znovu můžete buď vrátit zpět změny nebo zastavte a restartujte relaci ladění.  
  
 Ve Vizuálu C# v sadě Visual Studio nelze pomocí funkce upravit a pokračovat na žádný kód v metodě, která obsahuje datovou sadu dotazu LINQ to.  
  
 V jazyce Visual Basic v sadě Visual Studio můžete upravit a pokračovat na jiný než LINQ na datovou sadu kód, dokonce i v metodě, která obsahuje datovou sadu dotazu LINQ to. Můžete přidat nebo odebrat kód před LINQ to DataSet příkaz i v případě, že změny ovlivní počet řádků dotazu LINQ to DataSet. V jazyce Visual Basic prostředí ladění pro jiný než LINQ k datové sadě kód zůstává stejná jako před zavedením LINQ k datové sadě. Nelze změnit, přidat nebo odebrat LINQ to DataSet dotazu, ale pokud zastavíte ladění, aby se změny projevily.  
  
## <a name="see-also"></a>Viz také:

- [Ladění spravovaného kódu](/visualstudio/debugger/debugging-managed-code)
- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
