---
title: My.resources – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 02e29b17404da0e868973364b0b17b5c4ca418c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647630"
---
# <a name="myresources-object"></a>My.Resources – objekt
Poskytuje třídy a vlastnosti pro přístup k prostředkům aplikace.  
  
## <a name="remarks"></a>Poznámky  
 `My.Resources` Objekt poskytuje přístup k prostředkům vaší aplikace a umožňuje dynamicky načíst prostředky pro vaši aplikaci. Další informace najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
 `My.Resources` Zpřístupňuje pouze globální prostředky. Neposkytuje přístup k prostředku soubory spojené s formuláři. Musí přístup k prostředkům formuláře z formuláře.  
  
 Soubory prostředků specifické pro jazykovou verzi aplikace z dostanete `My.Resources` objektu. Ve výchozím nastavení `My.Resources` vyhledá prostředky ze zdrojového souboru, který odpovídá jazykové verze v objektu <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> vlastnost. Však můžete přepsat toto chování a určit konkrétní jazykové verze určený pro prostředky. Další informace najdete v tématu [prostředky v desktopových aplikací](../../../framework/resources/index.md).  
  
## <a name="properties"></a>Vlastnosti  
 Vlastnosti `My.Resources` objekt poskytují přístup jen pro čtení k prostředkům vaší aplikace. Chcete-li přidat nebo odebrat prostředky, použijte **Návrháře projektu**. Můžete mít přístup k prostředkům, které jsou přidány prostřednictvím **Návrháře projektu** pomocí `My.Resources.` *resourceName*.  
  
 Můžete také přidat nebo odebrat soubory prostředků tak, že vyberete projekt v **Průzkumníka řešení** a kliknete na **přidat novou položku** nebo **přidat existující položku** z  **Projekt** nabídky. Budete mít přístup k prostředkům přidat tímto způsobem s využitím `My.Resources.` *resourceFileName*`.`*resourceName*.  
  
 Každý prostředek má název, kategorie a hodnoty a tato nastavení prostředků určují, jak se zobrazí vlastnosti, která má přístup k prostředku v `My.Resources` objektu. Pro prostředky, přidá **Návrháře projektu**:  
  
- Určuje název, název vlastnosti,  
  
- Zdroj dat je hodnota vlastnosti,  
  
- Kategorie určuje typ vlastnosti:  
  
|Kategorie|Typ dat vlastnosti|  
|---|---|  
|**Řetězce**|[Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**Obrázky**|<xref:System.Drawing.Bitmap>|  
|**Ikony**|<xref:System.Drawing.Icon>|  
|**Zvuk**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream> Třída odvozena z <xref:System.IO.Stream> třídy, takže je možné pomocí metod, které berou datových proudů, jako například <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> metody.|  
|**Soubory**|-   [Řetězec](../../../visual-basic/language-reference/data-types/string-data-type.md) vyhledat textové soubory.<br />-   <xref:System.Drawing.Bitmap> pro soubory obrázků.<br />-   <xref:System.Drawing.Icon> pro soubory ikon.<br />-   <xref:System.IO.UnmanagedMemoryStream> zvukové soubory.|  
|**Jiné**|Určuje informace v okně Návrhář **typ** sloupce.|  
  
## <a name="classes"></a>Třídy  
 `My.Resources` Zpřístupňuje každého souboru prostředků jako třída s atributem sdílené vlastnosti. Název třídy je stejný jako název souboru prostředků. Jak je popsáno v předchozí části, prostředky do souboru prostředků jsou vystaveny jako vlastnosti ve třídě.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu nastaví název formuláře na prostředek řetězce s názvem `Form1Title` v souboru prostředků aplikace. Pro příklad fungoval, musí mít aplikace řetězec s názvem `Form1Title` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu nastaví ikony ve formuláři na ikonu s názvem `Form1Icon` , která je uložena v souboru prostředků aplikace. Pro příklad fungoval, musí mít aplikace ikonu s názvem `Form1Icon` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu nastaví obrázek na pozadí formuláře obrázkový prostředek s názvem `Form1Background`, což je v souboru prostředků aplikace. Pro tento příklad fungoval, musí aplikace mít obrázkový prostředek s názvem `Form1Background` v jeho souboru prostředků.  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu přehraje zvuk, který je uložený jako prostředek zvuku s názvem `Form1Greeting` v souboru prostředků aplikace. Například pro práci, aplikace musí mít zvukový prostředek s názvem `Form1Greeting` v jeho souboru prostředků. `My.Computer.Audio.Play` Metoda je k dispozici pouze pro aplikace Windows Forms.  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>Příklad  
 Tento příklad načte francouzské verzi řetězcový prostředek aplikace. Název prostředku `Message`. Změna jazykové verze, která `My.Resources` používá objekt, v příkladu <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>.  
  
 Pro tento příklad fungoval, musí mít aplikace řetězec s názvem `Message` v jeho prostředku souboru a aplikace by měla mít francouzština verzi souboru prostředků Resources.fr-FR.resx. Pokud aplikace nemá žádné francouzské verzi souboru prostředků `My.Resource` objekt získá prostředek ze souboru prostředků výchozí jazykové verze.  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [Prostředky v desktopových aplikacích](../../../framework/resources/index.md)
