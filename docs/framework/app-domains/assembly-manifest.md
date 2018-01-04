---
title: "Manifest sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41dc27798e9d39d391e5958b86f691e3a0062582
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-manifest"></a>Manifest sestavení
Všechna sestavení, zda statickou nebo dynamickou, obsahuje kolekci dat, která popisuje, jak elementů v sestavení vztahují k sobě navzájem. Manifest sestavení obsahuje tato metadata sestavení. Manifest sestavení obsahuje všechna metadata potřebná pro určení požadavky verze sestavení a zabezpečení identity a všechny metadata potřebná k definování oboru sestavení a odkazy na prostředky a třídy. Manifest sestavení může být uložená v buď PE soubor (příponou .exe nebo .dll) s kódem (MSIL intermediate language) Microsoft nebo v samostatný soubor PE, která obsahuje jenom manifestu informace o sestavení.  
  
 Následující obrázek znázorňuje, že mohou být uloženy různé způsoby manifest.  
  
 ![Jediný & č. 45; soubor sestavení](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")  
Typy sestavení  
  
 Manifest pro sestavení s jeden přidružený soubor, je součástí souboru PE a vytváří jeden soubor sestavení. Vícesouborového sestavení můžete vytvořit samostatný soubor manifestu nebo s manifest začleněná do jednoho ze souborů PE v sestavení.  
  
 Každý manifest sestavení provádí následující funkce:  
  
-   Vytvoří výčet soubory, které tvoří sestavení.  
  
-   Řídí, jak odkazy na sestavení typů a prostředků, mapování na soubory, které obsahují jejich deklarace a implementaci.  
  
-   Vytvoří výčet ostatních sestavení, na kterých závisí sestavení.  
  
-   Poskytuje úroveň dereference mezi spotřebiteli sestavení a podrobnosti implementace je sestavení.  
  
-   Vykreslí sestavení popisující samy sebe.  
  
## <a name="assembly-manifest-contents"></a>Obsah manifestu sestavení  
 V následující tabulce jsou uvedeny informace obsažené v manifestu sestavení. První čtyři položky – název sestavení, číslo verze, jazykovou verzi a informace silný název – tvoří identity sestavení.  
  
|Informace o|Popis|  
|-----------------|-----------------|  
|Název sestavení|Textový řetězec určující název sestavení.|  
|Číslo verze|Hlavní verze a podverze číslo a číslo revize a sestavení. Modul CLR používá tato čísla k vynucení zásad správy verzí.|  
|Jazyková verze|Informace o jazykové verzi nebo jazyka sestavení podporuje. Tyto informace slouží jenom k označení sestavení jako satelitní sestavení obsahující informace o konkrétní jazykové verze nebo jazyk. (Sestavení s informací o jazykové verzi se automaticky předpokládá být satelitní sestavení.)|  
|Informace o silným názvem|Veřejný klíč od vydavatele, pokud nebyla zadána sestavení silným názvem.|  
|Seznam všech souborů v sestavení|Hodnota hash jednotlivých souborů obsažených v sestavení a název souboru. Všimněte si, že všechny soubory, které tvoří sestavení musí být ve stejném adresáři jako soubor obsahuje manifest sestavení.|  
|Informace o typu odkazu|Informace slouží k mapování typu odkaz na soubor, který obsahuje jeho deklaraci a implementaci modulem runtime. Používá se pro typy, které byly exportovány z sestavení.|  
|Informace v odkazovaných sestaveních|Seznam ostatních sestavení, které jsou staticky odkazuje sestavení. Každý odkaz obsahuje název závislého sestavení, metadata sestavení (verze, jazykové verze, operačního systému atd.) a veřejný klíč, pokud je silné název sestavení.|  
  
 Můžete přidat nebo změnit některé informace v manifestu sestavení pomocí atributů sestavení v kódu. Můžete změnit informace o verzi a informační atributů, včetně ochranné známky, Copyright, produktu, společnosti a informační verze. Úplný seznam atributů sestavení, najdete v části [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Viz také  
 [Obsah sestavení](../../../docs/framework/app-domains/assembly-contents.md)  
 [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
