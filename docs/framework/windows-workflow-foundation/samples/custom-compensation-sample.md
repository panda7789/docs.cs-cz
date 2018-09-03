---
title: Ukázková vlastní kompenzace
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475865"
---
# <a name="custom-compensation-sample"></a>Ukázková vlastní kompenzace
Tento příklad ukazuje způsob použití <xref:System.Activities.Statements.CompensableActivity> a její obslužná rutina kompenzace definovat vlastní kompenzační logiky. Scénář modelován v této ukázce je agentura pronájem nákladní vozidlo.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Kroky simulované jsou:  
  
1.  Požadavky uživatelů truck pronájem nabídky pro daného data.  
  
2.  Budou kontaktovány jako tři truck společnosti a jsou k dispozici tři uvozovky.  
  
3.  Uživatel vybere jednu nabídku truck a načte pořadí pomocí platební karty.  
  
4.  Aplikace zruší ostatní dva truck uvozovky.  
  
5.  Aplikace se účtuje poplatek za služby, který je nevratný neprémiové účty zrušení v případě 10 dní nebo méně než datum rezervaci.  
  
6.  Aplikace se účtuje poplatek pronájem nákladní vozidlo.  
  
7.  Aplikace čeká na datum rezervaci nebo dokud zákazníkovi se rozhodli zrušit rezervaci, podle toho, co nastane dřív.  
  
8.  Pokud zákazník zruší rezervace, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> vlastní kompenzační logiky bude spouštět podle následujícího postupu:  
  
    1.  Pokud má zákazník neprémiové účet a pak se stále bude účtovat poplatek za služby; je menší než 10 dní před datem rezervace v opačném případě aplikace náhrad servisní poplatek.  
  
    2.  Zbývající část kompenzovatelné aktivity (nákladní vozidlo pořadí + poplatek pořadí nákladní vozidlo) se spouštějí podle kompenzační logika výchozí, což je odpovídajícím způsobem upravit v obráceném pořadí spouštění.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete řešení CustomCompensation.sln. Je umístěn v adresáři \WF\Basic\Compensation\CustomCompensation.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Stisknutím kláves CTRL + F5 spusťte aplikaci.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`