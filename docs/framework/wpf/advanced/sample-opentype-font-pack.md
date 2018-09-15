---
title: Ukázková sada písem OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 93bba86801ec4971e884cb4703d7a6323a2e94fe
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45625825"
---
# <a name="sample-opentype-font-pack"></a>Ukázková sada písem OpenType
Toto téma obsahuje přehled ukázky [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma, které jsou distribuovány s [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)]. Rozšířená podpora písma ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] funkce, které mohou být využívána [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací.  
  
  
<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>V této sady sada písem OpenType je víc písem  
 [!INCLUDE[TLA2#tla_wcsdk](../../../../includes/tla2sharptla-wcsdk-md.md)] Poskytuje sadu ukázkových [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písem, které můžete použít při vytváření [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. Ukázka písma jsou dodávané v rámci licence od horní dotah Corporation. Těchto písmo implementovat pouze podmnožinu celkového funkce definované [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] formátu. Následující tabulka uvádí názvy vzorku [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma.  
  
|**Jméno**|**Soubor**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte tučného písma|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles světla|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero tučného písma|Pescab.ttf|  
  
 Následující obrázek znázorňuje, co ukázka [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] vypadat písma.  
  
 ![Seznam názvů písma v balík vzorových písmo](../../../../docs/framework/wpf/advanced/media/samplefontpack01.gif "samplefontpack01")  
V této sady sada písem OpenType je víc písem  
  
 Ukázka písma jsou dodávané v rámci licence od horní dotah Corporation. Horní dotah je poskytovatel produktů, pokročilé písma. Licence rozšířené nebo vlastní verze ukázka písma, najdete v článku [horní dotah Corporation webu](https://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
>  Jako vývojář je vaší povinností ujistit, že máte potřebná licenční oprávnění pro všechny písmo vložit do aplikace nebo jinak znovu distribuovat.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalace písem  
 Máte možnost nainstalovat vzorovou [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] písma na výchozí hodnotu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] adresář písma **\WINDOWS\Fonts**. Použijte ovládací panel písma k instalaci písem. Po těchto písmo v počítači, jsou přístupné pro všechny aplikace, které odkazují na výchozí [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] písma. Můžete zobrazit reprezentativní sadu znaků v několika velikostí písma zdvojnásobení – kliknutím na soubor písma. Následující snímek obrazovky ukazuje soubor Lindsey písma, Linds.ttf.  
  
 ![Písmo Lindsey &#40;OpenType&#41;](../../../../docs/framework/wpf/advanced/media/typographyinwpf-04.png "TypographyInWPF_04")  
Zobrazení Lindsey písma  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Použití písem  
 Existují dva způsoby, které můžete písem v aplikaci. Přidat písma do aplikace podle obsahu položky, které nejsou vloženy jako prostředky v rámci sestavení projektu. Alternativně můžete přidat písma do aplikace jako zdroj položek projektu, které jsou vloženy do souborů sestavení aplikace. Další informace najdete v tématu [balení písem s aplikacemi](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Typography>  
 [Funkce písma OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)  
 [Balení písem s aplikacemi](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
