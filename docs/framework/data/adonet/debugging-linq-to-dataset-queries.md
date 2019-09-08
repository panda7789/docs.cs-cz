---
title: Ladění dotazů v LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: a82fd3e99a556daf40e5c65a16cf20278f38ea26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785207"
---
# <a name="debugging-linq-to-dataset-queries"></a>Ladění dotazů v LINQ to DataSet

Visual Studio podporuje ladění kódu LINQ to DataSet. Existují však rozdíly mezi laděním LINQ to DataSet kódu a neLINQ to DataSetm spravovaného kódu. Většina funkcí ladění funguje s příkazy LINQ to DataSet, včetně krokování, nastavení zarážek a zobrazení výsledků, které se zobrazují v oknech ladicího programu. Odložené provádění dotazů v má však některé vedlejší účinky, které byste měli zvážit při ladění kódu LINQ to DataSet a existují určitá omezení pro použití operace Upravit a pokračovat. Toto téma popisuje aspekty ladění, které jsou jedinečné pro LINQ to DataSet v porovnání se spravovaným kódem bez LINQ to DataSet.  
  
## <a name="viewing-results"></a>Zobrazení výsledků  
 Výsledek LINQ to DataSet příkazu můžete zobrazit pomocí tipů, okno Kukátko a dialogového okna QuickWatch. Pomocí okna zdrojového kódu můžete pozastavit ukazatel na dotaz v okně zdroje a zobrazí se DataTip. Můžete zkopírovat LINQ to DataSet proměnnou a vložit ji do okno Kukátko nebo do dialogového okna QuickWatch. V LINQ to DataSet není dotaz vyhodnocen, je-li vytvořen nebo deklarován, ale pouze v případě, že je dotaz proveden. Tato operace se nazývá *odložené provedení*. Proto proměnná dotazu nemá hodnotu, dokud není vyhodnocena. Další informace najdete v tématu [dotazy v LINQ to DataSet](queries-in-linq-to-dataset.md).  
  
 Ladicí program musí vyhodnotit dotaz pro zobrazení výsledků dotazu. K tomuto implicitnímu vyhodnocení dochází při zobrazení LINQ to DataSet výsledek dotazu v ladicím programu a obsahuje některé efekty, které byste měli zvážit. Každé vyhodnocení dotazu trvá čas. Rozbalení uzlu výsledků trvá určitou dobu. U některých dotazů může opakované vyhodnocení způsobit znatelné snížení výkonu. Vyhodnocení dotazu může také způsobit vedlejší účinky, což jsou změny hodnoty dat nebo stavu programu. Ne všechny dotazy mají vedlejší účinky. Chcete-li zjistit, zda lze dotaz bezpečně vyhodnotit bez vedlejších účinků, je nutné pochopit kód, který implementuje dotaz. Další informace naleznete v tématu [vedlejší účinky a výrazy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Upravit a pokračovat  
 Upravit a pokračovat nepodporuje změny v LINQ to DataSetch dotazech. Pokud během relace ladění přidáte, odeberete nebo změníte příkaz LINQ to DataSet, zobrazí se dialogové okno s oznámením, že změnu není podporováno úpravou a pokračováním. V tomto okamžiku můžete vrátit změny nebo zastavit relaci ladění a restartovat novou relaci s upraveným kódem.  
  
 Kromě toho příkaz Upravit a pokračovat nepodporuje změnu typu nebo hodnoty proměnné, která je použita v příkazu LINQ to DataSet. Znovu můžete vrátit změny nebo zastavit a znovu spustit ladicí relaci.  
  
 V jazyce C# Visual Studio v aplikaci Visual Studio nelze použít příkaz Upravit a pokračovat pro žádný kód v metodě, která obsahuje LINQ to DataSet dotaz.  
  
 V Visual Basic v aplikaci Visual Studio můžete použít příkaz Upravit a pokračovat v kódu bez LINQ to DataSet, a to i v metodě, která obsahuje LINQ to DataSet dotaz. Můžete přidat nebo odebrat kód před příkazem LINQ to DataSet, a to i v případě, že změny ovlivňují číslo řádku LINQ to DataSet dotazu. Vaše prostředí pro Visual Basic ladění pro kód, který není LINQ to DataSet, zůstane stejné jako předtím, než bylo zavedeno LINQ to DataSet. LINQ to DataSet dotaz však nemůžete změnit, přidat ani odebrat, Pokud nezastavíte ladění, aby se změny projevily.  
  
## <a name="see-also"></a>Viz také:

- [Ladění spravovaného kódu](/visualstudio/debugger/debugging-managed-code)
- [Průvodce programováním](programming-guide-linq-to-dataset.md)
