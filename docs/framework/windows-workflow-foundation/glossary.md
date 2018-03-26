---
title: Glosář služby Windows Workflow Foundation pro rozhraní .NET Framework 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 54a0cc6d9a0c922e57bf00b649894f26b42a64f4
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Glosář služby Windows Workflow Foundation pro rozhraní .NET Framework 4.5
V dokumentaci k Windows Workflow Foundation se používají následující termíny.  
  
## <a name="terms"></a>Podmínky  
  
|Termín|Definice|  
|----------|----------------|  
|aktivita|Jednotka chování programu v modelu Windows Workflow Foundation. Jediné aktivity se může skládat společně na složitější aktivity.|  
|Akce aktivity|Datová struktura používá ke zveřejnění zpětných volání pro spuštění pracovního postupu a aktivity.|  
|Argument|Definuje tok dat do a z aktivity. Každý argument má zadaný směr: v, out nebo vstup/výstup. Tyto představují vstupní, výstupní a vstupní a výstupní parametry aktivity.|  
|Záložka|Bod, kdy aktivitu můžete pozastavit a počkejte být obnoven.|  
|kompenzace|Skupinu akcí, které jsou navržené tak, aby vrátit zpět nebo zmírnit účinku dříve dokončit práci.|  
|korelace|Tento mechanismus pro směrování zpráv do instance pracovního postupu nebo službě.|  
|výraz|Konstruktor, který přebírá jeden nebo více argumentů, provede operaci na argumentů a vrátí jednu hodnotu. Výrazy můžete použít všude, kde můžete použít aktivitu.|  
|Vývojový diagram|Zlepší dobře známé modelování, který představuje součástí programu jako symboly propojené společně s směrové šipky.  V rozhraní .NET Framework 4 můžete jako na vývojových diagramech pomocí aktivity vývojový diagram modelovat pracovních postupů.|  
|dlouho běžící proces|Jednotka spuštění programu, který nevrací okamžitě a můžou sahat restartování systému.|  
|uchování|Ukládají stav pracovního postupu nebo služby trvanlivého média, abyste mohli být uvolněna z paměti nebo obnovení po selhání systému.|  
|stav počítače|Dobře známé modelování zlepší představující součástí programu jako jednotlivé stavy propojené společně s přechodů mezi stavy založeného na událostech.  Pracovní postupy můžete modelován jako stav počítače pomocí StateMachine aktivity.|  
|látky|Představuje skupinu související záložky pod obecný identifikátor a umožňuje modulu runtime rozhodnutí o tom, jestli konkrétní záložku obnovení je platný nebo se může stát platný.|  
|převaděče typů|Typ CLR může být přidružen jeden nebo více System.ComponentModel.TypeConverter odvozených typů, které umožňují převodu instance typu CLR do a z instancí jiné typy. Typ converterr je spojena s typem CLR pomocí atributu System.ComponentModel.TypeConverterAttribute.  TypeConverterAttribute lze přímo na typ CLR nebo vlastnost. Převaděče typu zadaná u vlastnosti vždy má přednost před převaděč typ zadaný v typu CLR vlastnosti.|  
|proměnná|Představuje úložiště data, která musí být uloženy a získat přístup k později.|  
|pracovní postup|Jediné aktivity nebo stromu aktivit vyvolané hostitelském procesu.|  
|XAML|eXtensible Application Markup Language|
