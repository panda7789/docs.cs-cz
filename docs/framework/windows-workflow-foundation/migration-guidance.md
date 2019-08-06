---
title: Pokyny pro migraci
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 45f81b29f63701f690e396de2e9834f9933fd775
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796800"
---
# <a name="migration-guidance"></a>Pokyny pro migraci
[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]V Microsoft uvolňuje druhá hlavní verze programovací model Windows Workflow Foundation (WF). [!INCLUDE[wf1](../../../includes/wf1-md.md)]byla vydaná v WinFX (to zahrnuje typy v System. Workflow.\* Namespaces; teď označované jako WF3) a rozšířené v. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] WF3 je také součástí [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ale existuje společně s novou technologií pracovního postupu (typy v System. Activities.\* Namespaces; označované jako WF4). Při zvažování, kdy přijmout WF4, je důležité nejprve rozpoznat, že budete řídit časování.  
  
- WF3 je plně podporovaná část [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].  
  
- Aplikace WF3 běží na [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bez úprav a jsou nadále plně podporované.  
  
- Je možné vytvořit nové aplikace WF3 a stávající aplikace lze upravovat v aplikaci Visual Studio 2012 a jsou plně podporovány.  
  
 Proto rozhodnutí o přijetí .NET Framework 4 se oddělí od vašeho rozhodnutí o přesun do WF4 (System. Activities.\*) z WF3 (System. Workflow.\*). Toto téma obsahuje odkazy na pokyny k migraci WF, které poskytují informace o práci s WF3 a WF4.  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a>Dokumenty White paper k migraci WF a návody  
 Téma [Přehled migrace WF](https://go.microsoft.com/fwlink/?LinkId=153873) poskytuje širokou škálu vztahů mezi WF3 a WF4 a strategiemi migrace. Doprovodná témata se podrobněji přecházení na konkrétní témata.  
  
 [Přehled migrace WF](https://go.microsoft.com/fwlink/?LinkId=153873)  
 Popisuje vztah mezi WF3 a WF4 a možnostmi, které máte jako uživatel nebo potenciální uživatel technologie pracovního postupu v rozhraní .NET 4.  
  
 [Migrace WF: Osvědčené postupy pro vývoj WF3](https://go.microsoft.com/fwlink/?LinkId=153852)  
 Popisuje, jak navrhovat artefakty WF3, aby je bylo možné snadněji migrovat na WF4.  
  
 [Návod k WF: Pravidly](https://go.microsoft.com/fwlink/?LinkId=153854)  
 Popisuje, jak přenést do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] řešení investice související s pravidly.  
  
 [Návod k WF: Stavový počítač](https://go.microsoft.com/fwlink/?LinkId=153855)  
 Popisuje modelování toku řízení WF4 při absenci aktivity stavového počítače.  
  
 Upozorňujeme, že tyto pokyny platí jenom pro projekty pracovního postupu, které cílí na .NET Framework 4. Pracovní postupy stavového počítače byly přidány do .NET 4.0.1 s vydáním aktualizace platformy 1 a byly zahrnuty jako součást .NET Framework 4,5. Další informace o pracovních postupech stavových počítačů v .NET 4.0.1-4.0.3 a .NET Framework 4,5 najdete v tématu [aktualizace 4.0.1 pro součásti Microsoft .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) a [pracovní postupy stavového počítače](state-machine-workflows.md).  
  
 [Kuchařka Migrace WF: Vlastní aktivity](https://go.microsoft.com/fwlink/?LinkId=153856)  
 Poskytuje příklady a pokyny pro změnu návrhu WF3 vlastních aktivit na WF4.  
  
 [Kuchařka Migrace WF: Pokročilé vlastní aktivity](https://go.microsoft.com/fwlink/?LinkId=275560)  
 Poskytuje pokyny pro přenávrh pokročilých WF3 vlastních aktivit, které používají fronty WF3 a naplánování podřízených aktivit jako WF4 vlastní aktivity.  
  
 [Kuchařka Migrace WF: Zpracovávaný](https://go.microsoft.com/fwlink/?LinkId=153858)  
 Poskytuje příklady a pokyny pro přepracování pracovních postupů WF3 v WF4.  
  
 [Kuchařka Migrace WF: Hostování pracovního postupu](https://go.microsoft.com/fwlink/?LinkId=275561)  
 Poskytuje pokyny pro přepracování kódu hostování WF3 jako kódu hostování WF4. Cílem je pokrýt klíčové rozdíly v pracovních postupech hostujících mezi WF3 a WF4.  
  
 [Kuchařka Migrace WF: Sledování pracovního postupu](https://go.microsoft.com/fwlink/?LinkId=275562)  
 Poskytuje pokyny pro změnu návrhu kódu sledování WF3 a konfigurace pomocí ekvivalentního kódu a konfigurace sledování WF4.  
  
 [Návod k WF: Služby pracovních postupů](https://go.microsoft.com/fwlink/?LinkId=275564)  
 Poskytuje příklad podrobných pokynů pro přepracování pracovních postupů, které implementují webové služby Windows Communication Foundation (WCF), které jsou vytvořené v WF3 k použití WF4, pro běžné scénáře pro předem připravené služby. soutěž.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.Interop>
