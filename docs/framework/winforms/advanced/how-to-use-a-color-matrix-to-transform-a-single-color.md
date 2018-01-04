---
title: "Postupy: Použití matice barev k transformaci jedné barvy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6c9273102dc8e8f0fe6be3e31d0f0b6e570c7af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a>Postupy: Použití matice barev k transformaci jedné barvy
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulace s nimi bitové kopie. <xref:System.Drawing.Image>a <xref:System.Drawing.Bitmap> objekty jako 32bitové číslo úložiště barva každý pixelů: 8 bitů jednotlivých červená, zelená, modrá a alfa. Každý ze čtyř součástí je číslo od 0 do 255, kde 0 představuje žádné intenzitou a představující úplné intenzitou 255. Komponentu alfa Určuje průhlednost barvy: 0 je zcela průhledné a je plně neprůhledného 255.  
  
 Barva vektor je 4-řazené kolekce členů ve formuláři (červená, zelená, modrá, alpha). Například vektoru barvu (0, 255, 0, 255) představuje neprůhledného barvu, která nemá žádné red nebo blue, ale má zelená úplné intenzitou.  
  
 Jiné konvence pro představující barvy používá číslo 1 pro úplné intenzitou. Pomocí této konvence, by barvu popsané v předchozím odstavci reprezentované pomocí vektoru (0, 1, 0, 1). [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Při provádění transformací barev, používá jako úplné intenzitou konvenci 1.  
  
 Lineární transformace (otáčení, změnu velikosti a podobně) můžete použít barvu Vektorům vynásobením vektory barvu podle matice 4 x 4. Matice 4 x 4 však nelze použít pro překlad (nelineární). Pokud přidáte do každé vektorů barva fiktivní páté souřadnice (například číslo 1), můžete použít libovolnou kombinaci lineární transformace a překlady matice 5 × 5. Transformace skládající se z lineární transformace, za nímž následuje překlad nazývá afinní transformace.  
  
 Předpokládejme například, že chcete spustit s barvou (0,2, 0,0, 0.4, 1.0) a použít následující transformace:  
  
1.  Double red součásti  
  
2.  Přidání do komponenty červené, zelené a modré 0,2  
  
 Následující násobení matic provede dvojice transformace v uvedeném pořadí.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")  
  
 Elementy matice barev jsou indexované podle řádku a potom sloupce (počítáno od nuly). Například záznam v páté řádků a třetí sloupec matice M odlišené M [4] [2].  
  
 (Viz následující obrázek) matice identity 5 × 5 má hodnotami 1 na diagonálních a 0s everywhere else. Pokud jste barva vektoru vynásobit matice identity, barva vektoru se nezmění. Vhodný způsob k formuláři matice barev transformace je začínat matice identity a provedení malé změny, která vytvoří požadovanou transformaci.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")  
  
 Podrobnější diskuzi o matice a transformace, v tématu [systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má obrázek, který je všechny jedné barvy (0,2, 0,0, 0.4, 1.0) a použije transformaci popsané v předchozích odstavcích.  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii transformovaných na pravé straně.  
  
 ![Barvy](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")  
  
 Kód v následujícím příkladu používá k provedení přebarvení následující kroky:  
  
1.  Inicializace <xref:System.Drawing.Imaging.ColorMatrix> objektu.  
  
2.  Vytvoření <xref:System.Drawing.Imaging.ImageAttributes> objektu a předejte <xref:System.Drawing.Imaging.ColorMatrix> do objektu <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu.  
  
3.  Předat <xref:System.Drawing.Imaging.ImageAttributes> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
