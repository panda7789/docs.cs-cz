---
title: "My.Resources – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords: My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96e5b909d9945ed631cebe07e4cfc7d5dc2e019f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="myresources-object"></a>My.Resources – objekt
Poskytuje třídy a vlastnosti pro přístup k prostředkům aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Resources` Objekt poskytuje přístup k prostředkům aplikace a umožňuje dynamicky načíst prostředky pro vaši aplikaci. Další informace najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Objekt se poskytuje pouze globální prostředky. Neposkytuje přístup k prostředku soubory spojené s formuláři. Ve formuláři musí přístup k prostředkům formuláře.  
  
 Dostanete soubory specifické pro jazykovou verzi prostředků aplikace z `My.Resources` objektu. Ve výchozím nastavení `My.Resources` objekt vyhledává prostředky ze zdrojového souboru, který odpovídá jazykové verzi v <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> vlastnost. Můžete však toto chování potlačit a zadat konkrétní jazykovou verzi pro použití pro prostředky. Další informace najdete v tématu [prostředků v aplikacích plochy](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Resources` objekt poskytnout přístup jen pro čtení k prostředkům vaší aplikace. Chcete-li přidat nebo odebrat prostředky, použijte **Návrhář projektu**. Můžete přístup k prostředkům prostřednictvím přidány **Návrhář projektu** pomocí `My.Resources.``resourceName`.  
  
 Můžete také přidat nebo odebrat soubory prostředků výběrem projekt v **Průzkumníku řešení** a kliknutím na **přidat novou položku** nebo **přidat existující položku** z  **Projekt** nabídky. Dostanete prostředky přidali tímto způsobem, a to pomocí `My.Resources.``resourceFileName`.`resourceName`.  
  
 Každý prostředek, má název, kategorie a hodnoty, a tato nastavení prostředků určují, jak se zobrazuje vlastnosti, která má přístup k prostředku v `My.Resources` objektu. Pro prostředky v přidána **Návrhář projektu**:  
  
-   Určuje název, název vlastnosti  
  
-   Zdroj dat je hodnota vlastnosti  
  
-   Kategorie určuje typ vlastnosti:  
  
|Kategorie|Datový typ vlastnosti|  
|---|---|  
|**Řetězce**|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrázky**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Zvuk**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Třída odvozená z <xref:System.IO.Stream> třídy, takže ho můžete použít s metod, které berou datové proudy, jako například <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metoda.|  
|**Soubory**|-   [Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) textových souborů.<br />-   <xref:System.Drawing.Bitmap>pro soubory obrázků.<br />-   <xref:System.Drawing.Icon>pro soubory ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream>pro zvukové soubory.|  
|**Jiné**|Informace v Návrháři je dáno **typ** sloupce.|  
  
## <a name="classes"></a>Třídy  
 `My.Resources` Objekt poskytuje každý soubor prostředků jako třída sdílené vlastnostmi. Název třídy je stejný jako název souboru prostředků. Jak je popsáno v předchozí části, prostředky v souboru prostředků jsou zveřejněné jako vlastnosti ve třídě.  
  
## <a name="example"></a>Příklad  
 Tento příklad nastaví název ve tvaru, který na řetězec prostředku s názvem `Form1Title` v souboru prostředků aplikace. Například pro práci, musí mít aplikace řetězec s názvem `Form1Title` ve svém souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad nastaví ikona formuláře na ikonu s názvem `Form1Icon` který je uložený v souboru prostředků aplikace. Například pro práci, musí mít aplikace ikonu s názvem `Form1Icon` ve svém souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad nastaví obrázek na pozadí formuláře na bitovou kopii prostředků s názvem `Form1Background`, což je v souboru prostředků aplikace. Pro tento příklad fungoval, aplikace musí mít prostředek obrázku s názvem `Form1Background` ve svém souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad hraje zvuk, která je uložena jako zvukový prostředek s názvem `Form1Greeting` v souboru prostředků aplikace. Například pro práci, musí mít aplikace zvukový prostředek s názvem `Form1Greeting` ve svém souboru prostředků. `My.Computer.Audio.Play` Metoda je k dispozici pouze pro aplikace Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad načte francouzské verzi řetězce prostředků aplikace. Název prostředku `Message`. Chcete-li změnit jazykovou verzi, `My.Resources` používá objekt, příklad používá <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Pro tento příklad fungoval, musí mít aplikace řetězec s názvem `Message` v jeho prostředku souboru a aplikace by měla mít francouzské verzi souborů prostředků Resources.fr-FR.resx. Pokud aplikace nemá francouzské verzi souborů prostředků, `My.Resource` objekt načte prostředek ze zdrojového souboru pro výchozí jazykovou verzi.  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [Prostředky v desktopových aplikacích](../../../framework/resources/index.md)  

