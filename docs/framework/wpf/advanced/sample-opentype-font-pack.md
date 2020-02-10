---
title: Ukázková sada písem OpenType
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: be9bc6e0cddc0581b9acb319f7d1fc1c81dae268
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095109"
---
# <a name="sample-opentype-font-pack"></a>Ukázková sada písem OpenType
Toto téma poskytuje přehled ukázkových písem OpenType, která jsou distribuována s Windows SDK. Ukázková písma podporují rozšířené funkce OpenType, které mohou používat aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Písma v sadě Font Pack OpenType  
 Windows SDK poskytuje sadu ukázkových písem OpenType, které můžete použít při vytváření aplikací [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Ukázková písma se dodávají v rámci licence od společnosti Ascend Corporation. Tato písma implementují pouze podmnožinu celkových funkcí definovaných ve formátu OpenType. V následující tabulce jsou uvedeny názvy ukázkových písem OpenType.  
  
|**Název**|**File**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles světlo|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 Na následujícím obrázku vidíte, jak vypadají vzorová písma OpenType jako.  
  
 ![Seznam názvů písem v ukázkové sadě písem](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 Ukázková písma se dodávají v rámci licence od společnosti Ascend Corporation. Ascend je poskytovatel pokročilých produktů s písmy. Licence na rozšířené nebo vlastní verze ukázkových písem najdete na webu [společnosti Ascend 's Corporation](https://www.monotype.com/).  
  
> [!NOTE]
> Jako vývojář je vaše zodpovědnost za to, že máte požadovaná licenční práva pro všechna vložená písma do aplikace nebo jinak znovu distribuovat.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalace písem  
 Máte možnost nainstalovat ukázková písma OpenType do výchozího adresáře písem systému Windows **\WINDOWS\Fonts**. K instalaci písem použijte ovládací panel písma. Jakmile jsou tato písma ve vašem počítači, jsou přístupná pro všechny aplikace, které odkazují na výchozí písma Windows. Můžete zobrazit reprezentativní sadu znaků v různých velikostech písem tak, že kliknete na soubor písma. Následující snímek obrazovky ukazuje soubor písma Lindsey Linds. ttf.  
  
 ![Písmo OpenType &#40;písma Lindsey&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Zobrazení písma Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Používání písem  
 Existují dva způsoby, jak můžete v aplikaci používat písma. Do aplikace můžete přidat písma jako položky obsahu projektu, které nejsou vloženy jako prostředky v rámci sestavení. Alternativně můžete do aplikace přidat písma jako položky prostředků projektu, které jsou vloženy do souborů sestavení aplikace. Další informace najdete v tématu [balení písem s aplikacemi](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Documents.Typography>
- [Funkce písma OpenType](opentype-font-features.md)
- [Balení písem s aplikacemi](packaging-fonts-with-applications.md)
