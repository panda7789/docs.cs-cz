---
title: Manifest sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e87fdd31a4dfb9b595f165225f7b86d5e88ea7af
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607759"
---
# <a name="assembly-manifest"></a>Manifest sestavení
Všechna sestavení, zda statickou nebo dynamickou, obsahuje kolekci dat, která popisuje, jak prvky v sestavení vzájemně souvisí. Manifest sestavení obsahuje metadata toto sestavení. Manifest sestavení obsahuje všechna metadata potřebná k určení požadavky na verzi sestavení a zabezpečení identity a všechna metadata potřebná k určení oboru sestavení a odkazy na prostředky a třídy. Manifest sestavení mohou být uloženy v obou přenositelném Spustitelném souboru (příponou .exe nebo .dll) s kód Microsoft intermediate language (MSIL) nebo v samostatné přenositelného Spustitelného souboru, který obsahuje jenom informace o manifestu sestavení.  
  
 Následující obrázek znázorňuje, že mohou být uloženy různé způsoby, jak v manifestu.  
  
 ![Diagram, který obsahuje manifest v jednosouborového sestavení a konfigurace vícesouborové sestavení.](./media/assembly-manifest/assembly-types-diagram.gif)  
  
 V případě sestavení s jeden přidružený soubor manifestu součástí přenositelného Spustitelného souboru k vytvoření jednosouborového sestavení. Vícesouborová sestavení můžete vytvořit samostatný soubor manifestu nebo manifest do jednoho ze souborů PE v sestavení.  
  
 Každé sestavení manifestu provádí následující funkce:  
  
- Vytvoří výčet soubory, které tvoří sestavení.  
  
- Řídí, jak odkazy na typy a prostředky sestavení se mapují na soubory, které obsahují jejich deklarace a implementaci.  
  
- Jmenovitě uvádí jiná sestavení, na kterých závisí sestavení.  
  
- Poskytuje určitou úroveň dereference mezi spotřebiteli sestavení a podrobnosti implementace sestavení.  
  
- Vykresluje sestavení, která popisují samy sebe.  
  
## <a name="assembly-manifest-contents"></a>Obsah manifestu sestavení  
 V následující tabulce jsou uvedeny informace obsažené v manifestu sestavení. První čtyři položky, název sestavení, číslo verze, jazykovou verzi a informací o silném názvu – skládá z identity sestavení.  
  
|Informace o|Popis|  
|-----------------|-----------------|  
|Název sestavení|Textový řetězec určující název sestavení.|  
|Číslo verze|Číslo hlavní verze a podverze a číslo revize a sestavení. Modul common language runtime používá tato čísla k vynucení zásad správy verzí.|  
|Jazyková verze|Informace o jazykové verze nebo jazyka sestavení podporuje. Tyto informace by měla sloužit pouze k označení sestavení jako satelitní sestavení obsahující informace pro konkrétní jazykovou verzi nebo jazyk. (Sestavení s informací o jazykové verzi je automaticky předpokládá, že satelitní sestavení.)|  
|Informací o silném názvu|Veřejný klíč od vydavatele, pokud nebyla zadána sestavení silným názvem.|  
|Seznam všech souborů v sestavení|Hodnota hash jednotlivých souborů obsažených v sestavení a název souboru. Všimněte si, že všechny soubory, které tvoří sestavení musí být ve stejném adresáři jako soubor obsahující manifest sestavení.|  
|Informace o typu odkazu|Informace o používaných modulem runtime pro mapování typu odkazu na soubor, který obsahuje jeho deklaraci a implementaci. Používá se pro typy, které byly exportovány z sestavení.|  
|Informace v odkazovaných sestaveních|Seznam jiných sestavení, která staticky odkazuje sestavení. Každý odkaz obsahuje název závislého sestavení, metadata sestavení (verze, jazykovou verzi, operační systém a tak dále) a veřejný klíč, pokud je sestavení silný název.|  
  
 Můžete přidat nebo změnit některé informace v manifestu sestavení s použitím atributů sestavení ve vašem kódu. Můžete změnit informační atributy, včetně ochranné známky, autorská práva, produktu, společnosti a informační verze a informace o verzi. Úplný seznam atributů sestavení, naleznete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Viz také:

- [Obsah sestavení](../../../docs/framework/app-domains/assembly-contents.md)
- [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)
- [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Sestavení se silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md)
