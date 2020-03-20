---
title: Ukázková sada písem OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 30cb69fcf05108822e8f3e2d45c9e79dbced26ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181912"
---
# <a name="sample-opentype-font-pack"></a>Ukázková sada písem OpenType
Toto téma obsahuje přehled ukázkových písem OpenType, která jsou distribuována se sadou Windows SDK. Ukázková písma podporují rozšířené funkce OpenType, které mohou používat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  

<a name="overview"></a>
## <a name="fonts-in-the-opentype-font-pack"></a>Písma v balíčku písma OpenType  
 Sada Windows SDK poskytuje sadu ukázkových písem OpenType, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] které můžete použít při vytváření aplikací. Ukázková písma jsou dodávána na základě licence od společnosti Ascender Corporation. Tato písma implementují pouze podmnožinu celkových funkcí definovaných formátem OpenType. V následující tabulce jsou uvedeny názvy ukázkových písem OpenType.  
  
|**Název**|**Soubor**|  
|--------------|--------------|  
|Kootenay (Kootenay)|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Tučné|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles světlo|Pericl.ttf|  
|Pescadero (Pescadero)|Pesca.ttf|  
|Pescadero Tučné|Pescab.ttf|  
  
 Následující obrázek znázorňuje, jak vypadají ukázková písma OpenType.  
  
 ![Seznam názvů písem v ukázkovém balíčku písem](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Ukázková písma jsou dodávána na základě licence od společnosti Ascender Corporation. Ascender je poskytovatelem pokročilých produktů písma. Informace o licencování rozšířených nebo vlastních verzí ukázkových písem naleznete [na webu společnosti Ascender Corporation](https://www.monotype.com/).  
  
> [!NOTE]
> Jako vývojář je vaší odpovědností zajistit, abyste měli požadovaná licenční práva pro jakékoli písmo, které vložíte do aplikace nebo jinak redistribuujete.  
  
<a name="installing_the_fonts"></a>
## <a name="installing-the-fonts"></a>Instalace písem  
 Máte možnost nainstalovat ukázková písma OpenType do výchozího adresáře písem systému **Windows\WINDOWS\Fonts**. K instalaci písem použijte ovládací panel Písma. Jakmile jsou tato písma v počítači, jsou přístupná všem aplikacím, které odkazují na výchozí písma systému Windows. Reprezentativní sadu znaků v několika velikostech písma můžete zobrazit poklepáním na soubor písma. Následující snímek obrazovky ukazuje soubor písma Lindsey, Linds.ttf.  
  
 ![Lindsey písmo &#40;OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Zobrazení písma Lindsey  
  
<a name="using_the_fonts"></a>
## <a name="using-the-fonts"></a>Použití písem  
 Existují dva způsoby, které můžete použít písma v aplikaci. Písma můžete přidat do aplikace jako položky obsahu projektu, které nejsou vloženy jako prostředky v rámci sestavení. Alternativně můžete přidat písma do aplikace jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace. Další informace naleznete [v tématu Balení písem s aplikacemi](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Documents.Typography>
- [Funkce písma OpenType](opentype-font-features.md)
- [Balení písem s aplikacemi](packaging-fonts-with-applications.md)
