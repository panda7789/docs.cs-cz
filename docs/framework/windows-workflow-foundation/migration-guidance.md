---
title: Pokyny pro migraci
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 672ed1a93b4409f491d76ffeeaaac5f67a1c4b6e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802606"
---
# <a name="migration-guidance"></a>Pokyny pro migraci

V .NET Framework 4 Společnost Microsoft uvolňuje druhou hlavní verzi programovací model Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla vydána v WinFX (to zahrnuje typy v oborech názvů System. Workflow.\*, nyní označované jako WF3) a vylepšené v .NET Framework 3,5. WF3 je také součástí .NET Framework 4, ale existuje společně s novou technologií pracovního postupu (typy v oborech názvů System. Activities.\*, označované jako WF4). Při zvažování, kdy přijmout WF4, je důležité nejprve rozpoznat, že budete řídit časování.  
  
- WF3 je plně podporovaná součást .NET Framework 4.  
  
- Aplikace WF3 běží na .NET Framework 4 bez úprav a nadále jsou plně podporované.  
  
- Je možné vytvořit nové aplikace WF3 a stávající aplikace lze upravovat v aplikaci Visual Studio 2012 a jsou plně podporovány.  
  
 Proto se rozhodnutí o přijetí .NET Framework 4 oddělí od vašeho rozhodnutí o přesun do WF4 (System. Activities.\*) z WF3 (System. Workflow.\*). Toto téma obsahuje odkazy na pokyny k migraci WF, které poskytují informace o práci s WF3 a WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Dokumenty White paper k migraci WF a návody  
 Téma [Přehled migrace WF](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)) poskytuje širokou škálu vztahů mezi WF3 a WF4 a strategiemi migrace. Doprovodná témata se podrobněji přecházení na konkrétní témata.  
  
 [Přehled migrace WF](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Popisuje vztah mezi WF3 a WF4 a možnostmi, které máte jako uživatel nebo potenciální uživatel technologie pracovního postupu v rozhraní .NET 4.  
  
 [Migrace WF: osvědčené postupy pro vývoj WF3](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Popisuje, jak navrhovat artefakty WF3, aby je bylo možné snadněji migrovat na WF4.  
  
 [Pokyny k WF: pravidla](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Popisuje, jak přenést investice související s pravidly do řešení .NET Framework 4.  
  
 [Návod k WF: Stavový počítač](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Popisuje modelování toku řízení WF4 při absenci aktivity stavového počítače.  
  
 Upozorňujeme, že tyto pokyny platí jenom pro projekty pracovního postupu, které cílí na .NET Framework 4. Pracovní postupy stavového počítače byly přidány do .NET 4.0.1 s vydáním aktualizace platformy 1 a byly zahrnuty jako součást .NET Framework 4,5. Další informace o pracovních postupech stavových počítačů v .NET 4.0.1-4.0.3 a .NET Framework 4,5 najdete v tématu [aktualizace 4.0.1 pro součásti Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) a [pracovní postupy stavového počítače](state-machine-workflows.md).  
  
 [Migrace WF kuchařka: vlastní aktivity](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje příklady a pokyny pro změnu návrhu WF3 vlastních aktivit na WF4.  
  
 [Migrace WF kuchařka: pokročilé vlastní aktivity](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje pokyny pro přenávrh pokročilých WF3 vlastních aktivit, které používají fronty WF3 a naplánování podřízených aktivit jako WF4 vlastní aktivity.  
  
 [Migrace WF kuchařka: pracovní postupy](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje příklady a pokyny pro přepracování pracovních postupů WF3 v WF4.  
  
 [Migrace WF kuchařka: Hostování pracovního postupu](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje pokyny pro přepracování kódu hostování WF3 jako kódu hostování WF4. Cílem je pokrýt klíčové rozdíly v pracovních postupech hostujících mezi WF3 a WF4.  
  
 [Migrace WF kuchařka: sledování pracovního postupu](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje pokyny pro změnu návrhu kódu sledování WF3 a konfigurace pomocí ekvivalentního kódu a konfigurace sledování WF4.  
  
 [Pokyny k WF: služby pracovních postupů](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10))  
 Poskytuje příklad podrobných pokynů pro přepracování pracovních postupů, které implementují webové služby Windows Communication Foundation (WCF), které jsou vytvořené v WF3 k použití WF4, pro běžné scénáře pro předem připravené služby. soutěž.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.Interop>
