---
title: Manifest sestavení
description: Manifest sestavení .NET určuje požadavky na verzi, identitu zabezpečení a rozsah sestavení a informace pro řešení odkazů.
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
ms.openlocfilehash: 4f4d09f559ac66e1f3bc38af0781f7e01e7461d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380174"
---
# <a name="assembly-manifest"></a>Manifest sestavení
Každé sestavení, bez ohledu na to, zda statický nebo dynamický obsahuje kolekci dat, která popisuje, jak se prvky v sestavení vzájemně vztahují. Manifest sestavení obsahuje tato metadata sestavení. Manifest sestavení obsahuje všechna metadata potřebná k určení požadavků na verzi sestavení a identitu zabezpečení a veškerá metadata potřebná k definování rozsahu sestavení a rozpoznání odkazů na prostředky a třídy. Manifest sestavení může být uložen v souboru PE (soubor *. exe* nebo *. dll*) s kódem jazyka MSIL (Microsoft Intermediate Language) nebo v samostatném souboru PE, který obsahuje pouze informace o manifestu sestavení.  
  
 Následující obrázek ukazuje různé způsoby, jak lze manifest Uložit.  
  
 ![Diagram, který zobrazuje manifest v sestavení s jedním souborem a v konfiguraci vícesouborového sestavení.](./media/manifest/assembly-types-diagram.gif)  
  
 V případě sestavení s jedním přidruženým souborem je manifest začleněn do souboru PE za účelem vytvoření sestavení s jedním souborem. Můžete vytvořit vícesouborové sestavení se samostatným souborem manifestu nebo s manifestem integrovaným do jednoho ze souborů PE v sestavení.  
  
 Manifest každého sestavení provádí následující funkce:  
  
- Vytvoří výčet souborů tvořících sestavení.  
  
- Určuje, jakým způsobem jsou odkazy na typy a prostředky sestavení mapovány na soubory, které obsahují jejich deklarace a implementace.  
  
- Vytvoří výčet jiných sestavení, na kterých závisí sestavení.  
  
- Poskytuje úroveň nepřímých odkazů mezi spotřebiteli sestavení a podrobnostmi implementace sestavení.  
  
- Vykreslí sestavení samy s popisem.  
  
## <a name="assembly-manifest-contents"></a>Obsah manifestu sestavení  
 V následující tabulce jsou uvedeny informace obsažené v manifestu sestavení. První čtyři položky: název sestavení, číslo verze, jazyková verze a informace o silných názvech tvoří identitu sestavení.  
  
|Informace|Popis|  
|-----------------|-----------------|  
|Název sestavení|Textový řetězec, který určuje název sestavení.|  
|Číslo verze|Číslo hlavní verze a podverze a číslo revize a buildu. Modul CLR (Common Language Runtime) používá tato čísla k vymáhání zásad verze.|  
|Kultura|Informace o jazykové verzi nebo jazyku, který sestavení podporuje. Tyto informace by měly být použity pouze k určení sestavení jako satelitního sestavení, které obsahuje jazykovou verzi nebo informace specifické pro jazyk. (Sestavení s informacemi o jazykové verzi se automaticky předpokládá jako satelitní sestavení.)|  
|Informace o silných názvech|Veřejný klíč od vydavatele, pokud se sestavení dostalo silný název.|  
|Seznam všech souborů v sestavení|Hodnota hash jednotlivých souborů obsažených v sestavení a název souboru. Všimněte si, že všechny soubory, které tvoří sestavení, musí být ve stejném adresáři jako soubor obsahující manifest sestavení.|  
|Referenční informace o typu|Informace používané modulem runtime k mapování odkazu na typ souboru, který obsahuje jeho deklaraci a implementaci. Tento typ se používá pro typy, které jsou exportovány ze sestavení.|  
|Informace o odkazovaných sestaveních|Seznam dalších sestavení, která jsou staticky odkazována sestavením. Každý odkaz obsahuje název závislého sestavení, metadata sestavení (verze, jazyková verze, operační systém atd.) a veřejný klíč, pokud je sestavení silným názvem.|  
  
 Můžete přidat nebo změnit některé informace v manifestu sestavení pomocí atributů sestavení v kódu. Můžete změnit informace o verzi a informativní atributy, včetně ochranných známek, autorských práv, produktů, společnosti a informativní verze. Úplný seznam atributů sestavení naleznete v tématu [set Assembly Attributes](set-attributes.md).  
  
## <a name="see-also"></a>Viz také

- [Obsah sestavení](contents.md)
- [Správa verzí sestavení](versioning.md)
- [Vytváření satelitních sestavení](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [Sestavení se silným názvem](strong-named.md)
