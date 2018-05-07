---
title: Pokyny pro migraci
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 562ee0913f657b349d88fe7be1627ecd9469f317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="migration-guidance"></a>Pokyny pro migraci
V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], společnost Microsoft vydává druhý hlavní verzi Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla vydána v [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (to zahrnuté typy v oborech názvů System.Workflow.* barvy; nyní označuje jako WF3) a rozšířené v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. WF3 je také součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale existuje existuje souběžně s novou technologií pracovního postupu (typy v systém.\* obory názvů; označuje jako WF4). Při určování, kdy se mají přijmout WF4, je potřeba nejdřív rozpoznat řídit načasování.  
  
-   WF3 je plně podporovaný součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
-   WF3 aplikace spustit na [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez úprav a dále plně podporována.  
  
-   Můžete vytvořit nové aplikace WF3 a existující aplikace lze upravit v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] a jsou plně podporovány.  
  
 Proto je rozhodnutí o přijetí rozhraní .NET Framework 4 odpojené od vaše rozhodnutí pro přesun do WF4 (System.Activities.*) z WF3 (System.Workflow.\*). Toto téma obsahuje odkazy na pokyny k migraci WF, které obsahuje informace o práci s WF3 a WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Dokumenty White paper Migrace WF a Cookbooks  
 [Přehled migrace WF](http://go.microsoft.com/fwlink/?LinkId=153873) tématu poskytuje komplexní přehled o vztah mezi WF3 a WF4 a migrace strategie. Témata Průvodce vyhledáváním, přejdete na konkrétní témata.  
  
 [Přehled migrace WF](http://go.microsoft.com/fwlink/?LinkId=153873)  
 Popisuje vztah mezi WF3 a WF4 a volby, měli byste jako uživatel nebo potenciální uživatel technologie pracovního postupu v rozhraní .NET 4.  
  
 [WF migrace: Osvědčené postupy pro vývoj WF3](http://go.microsoft.com/fwlink/?LinkId=153852)  
 Popisuje, jak navrhnout WF3 artefakty, mohou být snadněji migrovány do WF4.  
  
 [WF pokyny: pravidla](http://go.microsoft.com/fwlink/?LinkId=153854)  
 Popisuje, jak převést související pravidla investice předat do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] řešení.  
  
 [WF pokyny: Stav počítače](http://go.microsoft.com/fwlink/?LinkId=153855)  
 Popisuje tok řízení WF4 modelování chybí aktivitu stav počítače.  
  
 Všimněte si, že v tomto návodu se aplikuje jenom na projekty workflow, které cílí na rozhraní .NET Framework 4. Pracovní postupy stavu počítače byly přidány v rozhraní .NET 4.0.1 s vydáním Platform Update 1 a byly součástí rozhraní .NET Framework 4.5. Další informace o stavu počítače pracovních postupů v rozhraní .NET 4.0.1 - 4.0.3 a rozhraní .NET Framework 4.5, najdete v části [aktualizace 4.0.1 pro rozhraní Microsoft .NET Framework 4 funkce](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) a [stavu počítače pracovních](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
 [WF kuchařka migrace: Vlastní aktivity](http://go.microsoft.com/fwlink/?LinkId=153856)  
 Poskytuje pokyny pro přepracování WF3 vlastní aktivity na WF4 a příklady.  
  
 [WF kuchařka migrace: Pokročilé vlastní aktivity](http://go.microsoft.com/fwlink/?LinkId=275560)  
 Obsahuje pokyny pro přepracování pokročilé vlastní aktivity WF3, které používají fronty WF3 a plán podřízené aktivity jako WF4 vlastní aktivity.  
  
 [WF migrace kuchařka: pracovní postupy](http://go.microsoft.com/fwlink/?LinkId=153858)  
 Poskytuje pokyny pro přepracování WF3 pracovních postupů na WF4 a příklady.  
  
 [WF kuchařka migrace: Hostování pracovního postupu](http://go.microsoft.com/fwlink/?LinkId=275561)  
 Obsahuje pokyny pro přepracování WF3 hostování kód jako WF4 hostování kódu. Cílem je tak, aby pokrývalo hlavní rozdíly ve hostování mezi WF3 a WF4 pracovního postupu.  
  
 [WF kuchařka migrace: Sledování pracovní postup](http://go.microsoft.com/fwlink/?LinkId=275562)  
 Obsahuje pokyny pro přepracování WF3 sledování kódu a konfigurace pomocí ekvivalentní WF4 sledování kódu a konfigurace.  
  
 [WF pokyny: Služby pracovních postupů](http://go.microsoft.com/fwlink/?LinkId=275564)  
 Poskytuje příklad orientované podrobné pokyny pro pracovní postupy, které implementují Windows Communication Foundation (WCF) webové služby (obvykle označuje jako služeb pracovních postupů) vytvořené v WF3 použití WF4, pro běžné scénáře pro out-of-box přepracování aktivity.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.Interop>
