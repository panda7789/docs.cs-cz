---
title: Balení a nasazení vlastních rozšíření
ms.date: 08/14/2018
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
ms.openlocfilehash: a2e2a6705fb3d8d4424d46d96bbf49b41e1414af
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330262"
---
# <a name="package-and-deploy-custom-my-extensions-visual-basic"></a>Zabalit a nasadit vlastní moje rozšíření (Visual Basic)

Visual Basic poskytuje snadný způsob, jak nasadit vlastní rozšíření oboru názvů `My` pomocí šablon sady Visual Studio. Pokud vytváříte šablonu projektu, pro kterou jsou rozšíření `My` nedílnou součástí nového typu projektu, můžete při exportu šablony přidat do projektu vlastní kód rozšíření `My`. Další informace o exportu šablon projektů naleznete v tématu [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).

Pokud je vaše vlastní `My` rozšíření v jednom souboru kódu, můžete soubor exportovat jako šablonu položky, kterou mohou uživatelé přidat do libovolného typu Visual Basic projektu. Pak můžete přizpůsobit šablonu položky a povolit tak další možnosti a chování pro vlastní rozšíření `My` v projektu Visual Basic. Mezi tyto možnosti patří následující:

- Umožnění uživatelům spravovat vlastní rozšíření `My` ze stránky **Moje rozšíření** v návrháři projektu Visual Basic.

- Automatické přidání vlastního rozšíření `My`, když se do projektu přidá odkaz na zadané sestavení.

- Skryje šablonu položky rozšíření `My` v dialogovém okně **Přidat položku** tak, že není obsažena v seznamu položek projektu.

Toto téma popisuje, jak zabalit vlastní rozšíření `My` jako skrytou šablonu položky, kterou lze spravovat ze stránky **Moje rozšíření** v návrháři projektu Visual Basic. Vlastní rozšíření `My` lze také přidat automaticky, pokud je do projektu přidán odkaz na zadané sestavení.

## <a name="create-a-my-namespace-extension"></a>Vytvoření rozšíření My Namespace

Prvním krokem při vytváření balíčku pro nasazení pro vlastní rozšíření `My` je vytvořit rozšíření jako jeden soubor kódu. Podrobnosti a pokyny, jak vytvořit vlastní rozšíření `My`, najdete v tématu [rozšíření oboru názvů My v Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).

## <a name="export-a-my-namespace-extension-as-an-item-template"></a>Exportovat rozšíření My Namespace jako šablonu položky

Až budete mít soubor kódu, který obsahuje `My` rozšíření oboru názvů, můžete soubor kódu exportovat jako šablonu položky sady Visual Studio. Pokyny, jak exportovat soubor jako šablonu položky sady Visual Studio, naleznete v tématu [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).

> [!NOTE]
> Pokud má rozšíření oboru názvů `My` závislost na konkrétní sestavení, můžete přizpůsobit šablonu položky tak, aby automaticky instalovala rozšíření oboru názvů `My` při přidání odkazu na toto sestavení. V důsledku toho budete chtít vyloučit tento odkaz na sestavení, když exportujete soubor kódu jako šablonu položky sady Visual Studio.

## <a name="customize-the-item-template"></a>Přizpůsobení šablony položky

Šablonu položky můžete povolit, aby byla spravována ze stránky **Moje rozšíření** návrháře projektu Visual Basic. Můžete také povolit automatické přidání šablony položky, když je do projektu přidán odkaz na zadané sestavení. Chcete-li povolit tato přizpůsobení, přidejte do šablony nový soubor, označovaný jako soubor CustomData, a poté přidejte nový prvek do XML v souboru. vstemplate.

### <a name="add-the-customdata-file"></a>Přidat soubor CustomData

Soubor CustomData je textový soubor, který má příponu názvu souboru. CustomData (název souboru může být nastaven na libovolnou hodnotu smysluplnou pro šablonu) a obsahující XML. KÓD XML v souboru CustomData nastaví Visual Basic, aby zahrnoval rozšíření `My`, když uživatelé použijí stránku **Moje rozšíření** návrháře projektu Visual Basic. Volitelně můžete přidat atribut <`AssemblyFullName>` do souboru XML CustomData. Tato pokyny Visual Basic k automatické instalaci vlastního rozšíření `My`, když je do projektu přidán odkaz na konkrétní sestavení. Pomocí libovolného textového editoru nebo editoru XML můžete vytvořit soubor CustomData a pak ho přidat do komprimované složky šablony položky (soubor ZIP).

Například následující kód XML ukazuje obsah souboru CustomData, který přidá položku šablony do složky Moje rozšíření v projektu Visual Basic, když se do projektu přidá odkaz na sestavení Microsoft. VisualBasic. PowerPacks. vs. dll.

```xml
<VBMyExtensionTemplate
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"
    Version="1.0.0.0"
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"
/>
```

Soubor CustomData obsahuje prvek <`VBMyExtensionTemplate>`, který má atributy uvedené v následující tabulce.

|Atribut|Popis|
|---|---|
|`ID`|Požadováno. Jedinečný identifikátor pro rozšíření. Pokud rozšíření s tímto ID již bylo do projektu přidáno, uživatel nebude vyzván k jeho přidání.|
|`Version`|Požadováno. Číslo verze pro šablonu položky|
|`AssemblyFullName`|Volitelná. Název sestavení. Pokud je do projektu přidán odkaz na toto sestavení, bude uživatel vyzván k přidání rozšíření `My` z této šablony položky.|

### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a>Přidat prvek \<CustomDataSignature – > do souboru. vstemplate

Chcete-li identifikovat šablonu položky sady Visual Studio jako `My` rozšíření oboru názvů, je nutné také upravit soubor. vstemplate pro šablonu položky. Do elementu `<TemplateData>` je nutné přidat prvek `<CustomDataSignature>`. Element `<CustomDataSignature>` musí obsahovat text `Microsoft.VisualBasic.MyExtension`, jak je znázorněno v následujícím příkladu.

```xml
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>
```

Soubory nelze upravovat v komprimované složce (soubor. zip) přímo. Je nutné zkopírovat soubor. vstemplate z komprimované složky, upravit ho a pak nahradit soubor. vstemplate v komprimované složce pomocí aktualizované kopie.

Následující příklad ukazuje obsah souboru. vstemplate, který má přidané `<CustomDataSignature>` element.

```xml
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
  <TemplateData>
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>
    <Name>MyPrinterInfo</Name>
    <Description>Custom My Extensions Item Template</Description>
    <ProjectType>VisualBasic</ProjectType>
    <SortOrder>10</SortOrder>
    <Icon>__TemplateIcon.ico</Icon>
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>
  </TemplateData>
  <TemplateContent>
    <References />
    <ProjectItem SubType="Code"
                 TargetFileName="$fileinputname$.vb"
                 ReplaceParameters="true"
     >MyCustomExtensionModule.vb</ProjectItem>
  </TemplateContent>
</VSTemplate>
```

## <a name="install-the-template"></a>Instalace šablony

Chcete-li nainstalovat šablonu, můžete zkopírovat komprimovanou složku (soubor *. zip* ) do složky šablony Visual Basic položek. Ve výchozím nastavení se šablony uživatelských položek nacházejí v *%UserProfile%\Documents\Visual studiu \<verze\>\Templates\ItemTemplates\Visual Basic*. Alternativně můžete šablonu publikovat jako soubor Instalační program pro Visual Studio ( *. vsi*).

## <a name="see-also"></a>Viz také:

- [Rozšíření oboru názvů My v Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)
- [Rozšíření aplikačního modelu jazyka Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [Přizpůsobení výběru objektů dostupných v oboru názvů My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [Stránka Moje rozšíření, Návrhář projektu](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
