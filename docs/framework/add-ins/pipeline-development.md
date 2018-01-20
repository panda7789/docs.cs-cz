---
title: "Vývoj kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add-in pipeline [.NET Framework], segments
- activation path for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], activation path
- communication pipeline for add-ins [.NET Framework]
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], pipeline development
ms.assetid: 932788f2-b87d-44cf-82f9-04492a8b2722
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33646bbd7b0043cb5fc036b9b11aa4cf37cd537f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="pipeline-development"></a>Vývoj kanálu
Kanál doplňku je cesta kanálu segmentů, které hostitelskou aplikaci a její add-in musí používat ke komunikaci mezi sebou.  
  
 Následující obrázek znázorňuje komunikační kanál a jeho segmentů.  
  
 ![Přidat & č. 45; ve model kanálu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Kanál doplňku  
  
 Doplněk je na druhém konci hostitelskou aplikaci je na jednom konci kanálu. Spuštění z obou koncích a přesun do středu, hostitelskou aplikaci i v doplňku mají abstraktní základní třída, která definuje zobrazení objektu modelu, který obě sdílejí. Tyto typy (třídy) tvoří segmentu kanálu doplněk zobrazení a zobrazení hostitele segmentu doplněk kanálu. Segment kanálu doplněk zobrazení často obsahuje více než jeden abstraktní třídu, ale třídu, která v doplňku dědí z se označuje jako základní add-in.  
  
 Segment kanálu přidat straně adaptéru a adaptér hostitelské kanálu segment převést toku typy mezi segmenty kanálu jejich zobrazení a segment kanálu kontrakt. Centrální segment kanálu je kontrakt, který je odvozený od <xref:System.AddIn.Contract.IContract> rozhraní. Tento kontrakt definuje metody, které hostitelskou aplikaci a její doplněk obě použije.  
  
 Pokud hostitel a doplněk načíst do samostatné aplikační domény, musíte hranici izolace, která odděluje portál oboru hostitelskou aplikaci z oboru add-in. Kontrakt je pouze sestavení, který je načten do hostitele a domény doplňku aplikace. Hostitele a doplněk každý se vztahují pouze jejich zobrazení metod kontrakt. Proto jsou odděleny úroveň abstrakce ze smlouvy.  
  
 Vývoj kanálu segmenty, musíte vytvořit strukturu adresáře, která bude obsahovat. Další informace o požadavky na vývoj a oboru pokyny najdete v tématu [požadavky na vývoj kanálu](http://msdn.microsoft.com/library/ef9fa986-e80b-43e1-868b-247f4c1d9da5).  
  
 Následující obrázek znázorňuje typy, které tvoří segmenty kanálu. Názvy typů znázorněno na obrázku jsou libovolný, ale všechny typy s výjimkou hostitele a hostitele zobrazení atributů vyžadovat add-in, může být zjištěny pomocí metody, které vytvořit úložišti informace.  
  
 ![Přidat & č. 45; v modelu s povinné atributy pro typy. ] (../../../docs/framework/add-ins/media/addin-model.png "AddIn_Model")  
Doplněk s typy  
  
 Následující tabulka popisuje segmenty kanálu pro aktivaci doplňku. Další informace o tyto segmenty najdete v tématu [kontrakty, zobrazení a adaptéry](http://msdn.microsoft.com/library/a6460173-9507-4b87-8c07-d4ee245d715c).  
  
|Segment kanálu|Popis|  
|----------------------|-----------------|  
|Hostitel|Sestavení aplikace, které vytvoří instanci v.|  
|Doplněk zobrazení pro hostitele|Představuje hostitelskou aplikaci zobrazení typů objektů a metody používaný ke komunikaci s doplněk. Zobrazení hostitele je abstraktní základní třídu nebo rozhraní.|  
|Adaptér na straně hostitele|Sestavení s jednu nebo více tříd, které přizpůsobuje metody do a z kontrakt.<br /><br /> Tento kanál segment je určený podle pomocí <xref:System.AddIn.Pipeline.HostAdapterAttribute> atribut.<br /><br /> Více modul sestavení nejsou podporována.|  
|Kontrakt|Rozhraní, které je odvozený od <xref:System.AddIn.Contract.IContract> rozhraní a že definuje protokol pro komunikaci mezi hostitelem a jeho doplněk typy.<br /><br /> Tento kanál segment je určený podle nastavení <xref:System.AddIn.Pipeline.AddInContractAttribute> atribut.|  
|Přidat straně adaptéru|Sestavení s jednu nebo více tříd, které přizpůsobuje metody do a z kontrakt.<br /><br /> Tento kanál segment je určený podle pomocí <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut.<br /><br /> Každé sestavení v adresáři přidat straně adaptér, který obsahuje typ, který má <xref:System.AddIn.Pipeline.AddInAdapterAttribute> atribut je načten do doplňku pro doménu aplikace.<br /><br /> Každé sestavení v adresáři přidat straně je načíst v jeho vlastní domény aplikace.<br /><br /> Více modul sestavení nejsou podporovány.|  
|Přidejte v zobrazení|Sestavení, které představuje doplněk pro zobrazení typů objektů a metody, které se používají ke komunikaci s hostitelem. Na zobrazení je abstraktní základní třídu nebo rozhraní.<br /><br /> Tento kanál segment je určený podle pomocí <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut.<br /><br /> Každé sestavení v adresáři AddInViews, který obsahuje typ, který má <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut je načten do doplňku pro doménu aplikace.|  
|doplněk|Vytvořenou instanci typ, který provádí služba pro hostitele.|  
  
## <a name="pipeline-activation-path"></a>Aktivační cesta kanálu  
 Následující obrázek znázorňuje aktivace typů, když je aktivován doplňku. Také ukazuje předávání objektů na hostitele, třeba výsledky výpočtu nebo kolekce objektů. Toto je Nejobvyklejším scénářem.  
  
 ![Přidat & č. 45; v modelu s aktivační cesta. ] (../../../docs/framework/add-ins/media/addin6.png "AddIn6")  
Aktivační cesta z v doplňku na hostitele  
  
 Aktivační cesta kanálu dojde k následujícím způsobem:  
  
1.  Hostitelskou aplikaci aktivuje doplněk s <xref:System.AddIn.Hosting.AddInToken.Activate%2A> metoda.  
  
2.  Add-in a přidat v zobrazení, přidat straně adaptéru a kontrakt sestavení jsou načteny do doplňku pro doménu aplikace.  
  
3.  Instance adaptéru přidat straně je vytvořený pomocí tohoto zobrazení (pomocí třídy identifikovaný <xref:System.AddIn.Pipeline.AddInBaseAttribute> atribut) jako jeho konstruktoru. Přidat straně adaptér zdědí z kontrakt.  
  
4.  Přidat straně adaptér, který je zadán jako kontrakt, je přes hranici (volitelné) izolace předaný konstruktoru na straně hostitele adaptér.  
  
5.  Zobrazení hostitele add-in, hostitelské adaptéru, a kontrakt sestavení jsou načteny do domény aplikace hostitele.  
  
6.  Instance adaptéru hostitelské je vytvořený pomocí kontrakt jako jeho konstruktoru. Adaptér hostitelské dědí z pohledu hostitele add-in.  
  
7.  Hostitel má doplněk, který je zadán jako hostitel zobrazit add-in a můžete pokračovat volání její metody.  
  
## <a name="walkthroughs"></a>Postupy  
 Existují tři návod témata, které popisují, jak vytvořit tak kanály pomocí sady Visual Studio:  
  
-   [Návod: Vytváření rozšiřitelné aplikace](../../../docs/framework/add-ins/walkthrough-create-extensible-app.md)  
  
     Popisuje doplněk kalkulačky, který provádí sčítání, odčítání, násobení a dělení výpočty pro hostitele.  
  
-   [Návod: Povolení zpětné kompatibility jako hostitele změny](http://msdn.microsoft.com/library/6fa15bb5-8f04-407d-bd7d-675dc043c848)  
  
     Popisuje doplněk kalkulačky s možnostmi rozšířené výpočtu a postupy zachování kompatibility s první kalkulačky v aplikaci.  
  
-   [Návod: Předávání kolekce mezi hostiteli a doplňky](http://msdn.microsoft.com/library/b532c604-548e-4fab-b11c-377257dd0ee5)  
  
     Popisuje, jak předat kolekce dat přes kanál pomocí scénáři adresáře úložiště.  
  
## <a name="see-also"></a>Viz také  
 [Scénáře kanál doplňku](http://msdn.microsoft.com/library/feb70e0b-8734-494c-aeaf-b567f014043e)  
 [Doplňky a rozšíření](../../../docs/framework/add-ins/index.md)
