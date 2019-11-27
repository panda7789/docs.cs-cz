---
title: My.Resources – objekt
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 7f5d81194123ad2151a494a3cb79aa1955e0fdad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350329"
---
# <a name="myresources-object"></a>My.Resources – objekt
Poskytuje vlastnosti a třídy pro přístup k prostředkům aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `My.Resources` poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načítat prostředky pro vaši aplikaci. Další informace najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 Objekt `My.Resources` zpřístupňuje pouze globální prostředky. Neposkytuje přístup k souborům prostředků přidruženým k formulářům. Musíte získat přístup k prostředkům formuláře z formuláře.  
  
 Soubory prostředků specifické pro jazykovou verzi aplikace můžete přistupovat z objektu `My.Resources`. Ve výchozím nastavení objekt `My.Resources` vyhledá prostředky ze souboru prostředků, který odpovídá jazykové verzi ve vlastnosti <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>. Toto chování však můžete přepsat a zadat konkrétní jazykovou verzi, která se má použít pro prostředky. Další informace najdete v tématu [prostředky v aplikacích klasické pracovní plochy](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti objektu `My.Resources` poskytují přístup k prostředkům vaší aplikace jen pro čtení. Chcete-li přidat nebo odebrat prostředky, použijte **Návrháře projektu**. K prostředkům přidaným pomocí **Návrháře projektu** můžete přistupovat pomocí `My.Resources.`*resourceName*.  
  
 Můžete také přidat nebo odebrat soubory prostředků tak, že vyberete projekt v **Průzkumník řešení** a kliknete na **Přidat novou položku** nebo **Přidat existující položku** z nabídky **projekt** . Přístup k prostředkům přidaným tímto způsobem můžete získat pomocí `My.Resources.`*resourceFileName*`.`*resourceName*.  
  
 Každý prostředek má název, kategorii a hodnotu a tato nastavení prostředků určují, jak se vlastnost pro přístup k prostředku zobrazí v objektu `My.Resources`. Pro prostředky přidané v **Návrháři projektu**:  
  
- Název určuje název vlastnosti,  
  
- Data prostředku jsou hodnotou vlastnosti,  
  
- Kategorie určuje typ vlastnosti:  
  
|Kategorie|Datový typ vlastnosti|  
|---|---|  
|**Řetězce**|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrázky**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Zvuk**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> Třída <xref:System.IO.UnmanagedMemoryStream> je odvozena z <xref:System.IO.Stream> třídy, takže ji lze použít s metodami, které přijímají datové proudy, jako je například metoda <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>.|  
|**Soubory**|-   [řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) pro textové soubory.<br />pro soubory imagí -   <xref:System.Drawing.Bitmap>.<br />pro soubory ikon -   <xref:System.Drawing.Icon>.<br />pro zvukové soubory -   <xref:System.IO.UnmanagedMemoryStream>.|  
|**Jiné**|Určené podle informací ve sloupci **typ** návrháře.|  
  
## <a name="classes"></a>Třídy  
 Objekt `My.Resources` zpřístupňuje jednotlivé soubory prostředků jako třídu se sdílenými vlastnostmi. Název třídy je stejný jako název souboru prostředků. Jak je popsáno v předchozí části, prostředky v souboru prostředků jsou zveřejněny jako vlastnosti ve třídě.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se nastaví název formuláře na prostředek řetězce s názvem `Form1Title` v souboru prostředků aplikace. Aby příklad fungoval, musí mít aplikace řetězec s názvem `Form1Title` ve svém souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Tento příklad nastaví ikonu formuláře na ikonu s názvem `Form1Icon`, která je uložena v souboru prostředků aplikace. Aby mohl příklad fungovat, musí mít aplikace ikonu s názvem `Form1Icon` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se nastaví obrázek pozadí formuláře na prostředek obrázku s názvem `Form1Background`, který se nachází v souboru prostředků aplikace. Aby tento příklad fungoval, musí mít aplikace prostředek image s názvem `Form1Background` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Tento příklad hraje zvuk, který je uložen jako zvukový prostředek s názvem `Form1Greeting` v souboru prostředků aplikace. Aby příklad fungoval, musí mít aplikace zvukového prostředku s názvem `Form1Greeting` v jeho souboru prostředků. Metoda `My.Computer.Audio.Play` je k dispozici pouze pro model Windows Forms aplikace.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Tento příklad načte verzi zdrojového řetězce aplikace z francouzské kultury. Prostředek má název `Message`. Chcete-li změnit jazykovou verzi, kterou používá objekt `My.Resources`, používá tento příklad <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Aby tento příklad fungoval, musí mít aplikace řetězec s názvem `Message` ve svém souboru prostředků a aplikace by měla mít verzi francouzské jazykové verze tohoto souboru prostředků Resources.fr-FR. resx. Pokud aplikace nemá verzi francouzské jazykové verze souboru prostředků, objekt `My.Resource` načte prostředek ze souboru prostředků výchozí jazykové verze.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Prostředky v aplikacích klasické pracovní plochy](../../../framework/resources/index.md)
