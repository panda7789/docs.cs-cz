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
ms.openlocfilehash: 2b7c82c31d2e31ccbf573cf1dfa138af2d99ce29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372453"
---
# <a name="myresources-object"></a>My.Resources – objekt
Poskytuje vlastnosti a třídy pro přístup k prostředkům aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Resources`Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načítat prostředky pro vaši aplikaci. Další informace najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources`Objekt zpřístupňuje pouze globální prostředky. Neposkytuje přístup k souborům prostředků přidruženým k formulářům. Musíte získat přístup k prostředkům formuláře z formuláře.  
  
 Z objektu můžete získat přístup k souborům prostředků specifických pro jazykovou verzi aplikace `My.Resources` . Ve výchozím nastavení `My.Resources` objekt vyhledává prostředky ze souboru prostředků, který odpovídá jazykové verzi ve <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> Vlastnosti. Toto chování však můžete přepsat a zadat konkrétní jazykovou verzi, která se má použít pro prostředky. Další informace najdete v tématu [prostředky v aplikacích klasické pracovní plochy](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Resources` objektu poskytují přístup k prostředkům vaší aplikace jen pro čtení. Chcete-li přidat nebo odebrat prostředky, použijte **Návrháře projektu**. K prostředkům přidaným pomocí **Návrháře projektu** můžete přistupovat pomocí `My.Resources.` *resourceName*.  
  
 Můžete také přidat nebo odebrat soubory prostředků tak, že vyberete projekt v **Průzkumník řešení** a kliknete na **Přidat novou položku** nebo **Přidat existující položku** z nabídky **projekt** . K prostředkům přidaným tímto způsobem můžete přistupovat pomocí `My.Resources.` *resourceFileName* `.` *resourceName*.  
  
 Každý prostředek má název, kategorii a hodnotu a tato nastavení prostředků určují, jak se vlastnost pro přístup k prostředku zobrazí v `My.Resources` objektu. Pro prostředky přidané v **Návrháři projektu**:  
  
- Název určuje název vlastnosti,  
  
- Data prostředku jsou hodnotou vlastnosti,  
  
- Kategorie určuje typ vlastnosti:  
  
|Kategorie|Datový typ vlastnosti|  
|---|---|  
|**Řetězce**|[Řetězec](../data-types/string-data-type.md)|  
|**Image**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Zvuk**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>Třída je odvozena z <xref:System.IO.Stream> třídy, takže ji lze použít s metodami, které přijímají datové proudy, jako je například <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metoda.|  
|**Soubory**|-   [Řetězec](../data-types/string-data-type.md) pro textové soubory<br />-   <xref:System.Drawing.Bitmap>pro soubory obrázků.<br />-   <xref:System.Drawing.Icon>pro soubory ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream>pro zvukové soubory.|  
|**Jiné**|Určené podle informací ve sloupci **typ** návrháře.|  
  
## <a name="classes"></a>Třídy  
 `My.Resources`Objekt zpřístupňuje jednotlivé soubory prostředků jako třídu se sdílenými vlastnostmi. Název třídy je stejný jako název souboru prostředků. Jak je popsáno v předchozí části, prostředky v souboru prostředků jsou zveřejněny jako vlastnosti ve třídě.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se nastaví název formuláře na prostředek řetězce s názvem `Form1Title` v souboru prostředků aplikace. Aby příklad fungoval, musí mít aplikace řetězec s názvem `Form1Title` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Tento příklad nastaví ikonu formuláře na ikonu s názvem `Form1Icon` , která je uložena v souboru prostředků aplikace. Aby příklad fungoval, musí mít aplikace ikonu s názvem `Form1Icon` v souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se nastaví obrázek pozadí formuláře na prostředek obrázku s názvem `Form1Background` , který je v souboru prostředků aplikace. Aby tento příklad fungoval, musí mít aplikace prostředek image s názvem `Form1Background` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Tento příklad hraje zvuk, který je uložen jako zvukový prostředek s názvem `Form1Greeting` v souboru prostředků aplikace. Aby příklad fungoval, musí mít aplikace zvukového zdroje s názvem `Form1Greeting` v jeho souboru prostředků. `My.Computer.Audio.Play`Metoda je k dispozici pouze pro model Windows Forms aplikace.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Tento příklad načte verzi zdrojového řetězce aplikace z francouzské kultury. Prostředek se jmenuje `Message` . Chcete-li změnit jazykovou verzi, kterou `My.Resources` objekt používá, příklad používá <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> .  
  
 Aby tento příklad fungoval, musí mít aplikace řetězec s názvem `Message` ve svém souboru prostředků a aplikace by měla mít verzi francouzské jazykové verze tohoto souboru prostředků Resources.fr-fr. resx. Pokud aplikace nemá verzi souboru prostředků francouzské jazykové verze, `My.Resource` objekt načte prostředek ze souboru prostředků výchozí jazykové verze.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Viz také

- [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Prostředky v aplikacích klasické pracovní plochy](../../../framework/resources/index.md)
