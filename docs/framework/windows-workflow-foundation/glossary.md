---
title: Windows Workflow Foundation Glosář pro rozhraní .NET Framework 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], glossary
- WF [WF], glossary
ms.assetid: ab682b2f-3779-45ca-b831-b7c03d7dbb3a
ms.openlocfilehash: 61d9acab1161302937e240eb8ebb506ca9f1585c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482844"
---
# <a name="windows-workflow-foundation-glossary-for-net-framework-45"></a>Windows Workflow Foundation Glosář pro rozhraní .NET Framework 4.5

V dokumentaci k Windows Workflow Foundation se používají následující termíny.

## <a name="terms"></a>Podmínky

|Termín|Definice|
|----------|----------------|
|aktivita|Jednotka chování programu ve Windows Workflow Foundation. Jediné aktivity se může skládat dohromady na složitější aktivity.|
|aktivita akce|Datová struktura používaná k vystavení zpětná volání pro spouštění pracovních postupů a aktivit.|
|Argument|Definuje tok dat do a z aktivity. Každý argument má směr zadaný:, nebo v vstup a výstup. Ty představují vstupní, výstupní a vstupní a výstupní parametry aktivity.|
|záložky|Bod, jakou aktivitu můžete pozastavit a čekat na obnovit.|
|Kompenzace|Skupina akcí, které jsou navržené tak, aby vrácení zpět nebo zmírnit dopadu dříve dokončenou práci.|
|Korelace|Mechanismus pro směrování zpráv do instance služby nebo pracovního postupu.|
|výraz|Konstrukce, která přijímá jeden nebo více argumentů, provede operaci pro argumenty a vrací jedinou hodnotu. Výrazy můžete použít všude, kde lze použít aktivitu.|
|Vývojový diagram|Paradigma dobře známé modelování, který představuje součástí programu jako symboly propojené s směrové šipky.  V rozhraní .NET Framework 4 může být pracovních postupů nemodelují jako aktivitě Flowchart pomocí vývojových diagramů.|
|dlouho běžící proces|Jednotky provádění programu, který nevrací okamžitě a může zahrnovat restartování systému.|
|uchování|Ukládání stavu pracovního postupu nebo služby na trvalé médium, tak, aby může být uvolněna z paměti nebo obnovení po selhání systému.|
|Stavový stroj|Paradigma dobře známé modelování, který představuje součástí programu jako propojené s založený na událostech přechodů mezi stavy jednotlivých států.  Pracovní postupy lze modelovat jako stavu počítače, které používají aktivity StateMachine.|
|látky|Představuje skupinu související záložky v rámci obecný identifikátor a umožňuje modulu runtime k rozhodování o tom, jestli konkrétní záložku obnovení je platný nebo může být platný.|
|Konvertor typu|Typ CLR může být přidružený nejméně k jednomu nebo více System.ComponentModel.TypeConverter odvozené typy, které umožňují převod instance typu CLR do a z instance ostatních typů. Konvertor typu souvisí s typem CLR pomocí atributu System.ComponentModel.TypeConverterAttribute.  TypeConverterAttribute lze přímo na typ CLR nebo na vlastnost. Konvertor typu zadaný u vlastnosti vždy má přednost před konvertor typu určená na typu CLR vlastnosti.|
|proměnná|Reprezentuje úložiště data, která musí být uloženy a získat přístup později.|
|pracovní postup|Jediné aktivity nebo stromu aktivit vyvolávat hostitelský proces.|
|XAML|eXtensible Application Markup Language|
