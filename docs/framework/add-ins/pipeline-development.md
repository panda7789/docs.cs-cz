---
title: Vývoj kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 047cd7a2b8a6d315c6cadb9b535b84f744fd2d09
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504882"
---
# <a name="pipeline-development"></a>Vývoj kanálu
Kanál doplňku je cesta segmentů kanálu, které hostitelská aplikace a jeho doplňků musí používat ke komunikaci mezi sebou.  
  
 Následující obrázek znázorňuje komunikační kanál a jeho segmentů.  
  
 ![Přidat&#45;v kanálu modelu. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Kanál doplňku  
  
 Hostitelská aplikace je na jednom konci kanálu a doplňku je na druhém konci. Počínaje každý konec a přesun směrem do středu, hostitelské aplikace i doplňku mají abstraktní základní třídu, která definuje zobrazení objektu modelu, který ale i sdílet. Tyto typy (třídy) tvoří segment kanálu doplňku zobrazení a zobrazení hostitele doplňku kanálu segmentu. Segment kanálu doplňku zobrazení často obsahuje více než jednu abstraktní třídu, ale třída, která zdědí doplněk se označuje jako základ doplňku.  
  
 Segment kanálu adaptér přidat v na straně a převést segment kanálu adaptér hostitelské tok typy mezi jejich zobrazení segmentů kanálu a segment kanálu kontraktu. Centrální segment kanálu je kontrakt, který je odvozen z <xref:System.AddIn.Contract.IContract> rozhraní. Tento kontrakt definuje metody, které hostitelskou aplikaci a její doplňku se používají.  
  
 Pokud načtete hostitele a doplňku na samostatnou aplikační domény, je nutné oddělovací hranice, který odděluje oboru hostitelskou aplikaci z oboru add-in. Smlouva je pouze sestavení, který je načten do domény aplikace doplňku i hostitele. Hostitele a doplněk každý odkazovat pouze zobrazení svého kontraktu metody. Proto jsou odděleny abstrakční ze smlouvy.  
  
 K vývoji segmentů kanálu, musíte vytvořit adresářovou strukturu, která bude obsahovat. Další informace o požadavky na vývoj a pokyny pro obor, naleznete v tématu [požadavky na vývoj kanálu](https://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Následující obrázek znázorňuje typy, které tvoří segmentů kanálu. Názvy typů je znázorněno na obrázku jsou libovolného, ale všechny typy s výjimkou hostitele a hostitele zobrazení atributů doplněk vyžadovat, aby mohla být zjištěna metodami, které vytvořit úložiště informace.  
  
 ![Přidat&#45;v modelu s povinné atributy u typů. ](../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Kanál doplňku s typy  
  
 Následující tabulka popisuje segmentů kanálu pro aktivaci doplňku. Další informace o těchto segmentů, naleznete v tématu [kontrakty, zobrazení a adaptéry](https://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segment kanálu|Popis|  
|----------------------|-----------------|  
|Hostitel|Sestavení aplikace, která vytvoří instanci doplňku.|  
|Doplněk v zobrazení pro hostitele|Představuje zobrazení hostitelská aplikace objekt typů a metod používaných ke komunikaci s doplňku. Zobrazení hostitele je abstraktní základní třída nebo rozhraní.|  
|Adaptér na straně hostitele|Sestavení s jednu nebo více tříd, které se přizpůsobí metody do a ze smlouvy.<br /><br /> Tento segment kanálu je identifikovaný pomocí <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut.<br /><br /> Vícemodulová sestavení nejsou podporována.|  
|Kontrakt|Který je odvozen z rozhraní <xref:System.AddIn.Contract.IContract> rozhraní a, který definuje protokol pro komunikaci typů mezi hostitelem a jeho doplňku.<br /><br /> Tento segment kanálu je identifikován podle nastavení <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.|  
|Přidat v-adaptér na straně|Sestavení s jednu nebo více tříd, které se přizpůsobí metody do a ze smlouvy.<br /><br /> Tento segment kanálu je identifikovaný pomocí <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut.<br /><br /> Každé sestavení v adresáři adaptér přidat v na straně, který obsahuje typ, který má <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut je načten do doplňku na aplikační domény.<br /><br /> Každé sestavení v adresáři add-na straně je načteno do vlastní domény aplikace.<br /><br /> Sestavení s víc moduly se nepodporují.|  
|Zobrazení doplňku|Sestavení, který představuje zobrazení doplňku na typy objektů a metod, které se používají ke komunikaci s hostitelem. Zobrazení doplňku je abstraktní základní třída nebo rozhraní.<br /><br /> Tento segment kanálu je identifikovaný pomocí <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.<br /><br /> Každé sestavení v adresáři AddInViews, který obsahuje typ, který má <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut je načten do doplňku na aplikační domény.|  
|doplněk|Instance typu, který provádí služba pro hostitele.|  
  
## <a name="pipeline-activation-path"></a>Aktivační cesta kanálu  
 Následující obrázek znázorňuje aktivace typy, když se aktivuje doplněk. Také ukazuje předávání objektů na hostitele, jako jsou výsledky výpočtu nebo kolekci objektů. Toto je obvykle scénář.  
  
 ![Přidat&#45;v modelu s cestou k aktivaci. ](../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Aktivační cesta od doplňku na hostitele  
  
 Aktivační cesta kanálu dojde k následujícím způsobem:  
  
1.  Doplněk se aktivuje hostitelskou aplikaci <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metody.  
  
2.  Zobrazení doplňku, doplněk, adaptér přidat v na straně a sestavení kontraktu se načtou do doplňku na aplikační domény.  
  
3.  Pomocí zobrazení doplňku je vytvořena instance adaptér přidat v na straně (pomocí třídy identifikován <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut) jako jeho konstruktoru. Přidat v straně adaptér dědí ze smlouvy.  
  
4.  Přidat v straně adaptér, který je zadán jako kontrakt, je předána hranice izolace (volitelné) konstruktor adaptér na straně hostitele.  
  
5.  Zobrazení hostitele doplňku, hostitelské adaptéru a sestavení kontraktu jsou načtena do domény aplikací hostitele.  
  
6.  Pomocí kontraktu jako jeho konstruktor je vytvořena instance adaptér na straně hostitele. Adaptér na straně hostitele dědí ze zobrazení hostitele doplňku.  
  
7.  Hostitel má doplněk, který je zadán jako hostitele zobrazení doplňku a můžete pokračovat v jeho metody volání.  
  
## <a name="walkthroughs"></a>Postupy  
 Existují tři návody, které popisují, jak vytvářet kanály pomocí sady Visual Studio:  
  
-   [Návod: Vytváření rozšiřitelné aplikace](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Popisuje doplněk kalkulačky, který provádí sčítání, odčítání, násobení a dělení výpočtů pro hostitele.  
  
-   [Návod: Umožnění zpětné kompatibility při změně vašeho hostitele](https://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Popisuje doplněk Kalkulačka rozšířené výpočetní funkce a tom, jak udržovat kompatibilitu s první doplněk kalkulačky.  
  
-   [Návod: Předávání kolekcí mezi hostiteli a doplňky](https://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Popisuje, jak předat kolekce dat přes kanál pomocí scénář úložiště knihy.  
  
## <a name="see-also"></a>Viz také  
 [Scénáře kanálu doplňku](https://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Doplňky a rozšíření](../../../docs/framework/add-ins/index.md)
