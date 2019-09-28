---
title: 'Postupy: Odkazování na objekty modelu COM z Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 8e502dc9a279d9271a61fd2cf7a6afb564f09125
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351994"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Postupy: Odkazování na objekty modelu COM z Visual Basic
V Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů, vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM. Odkazy na členy objektu COM jsou směrovány do sestavení vzájemné spolupráce a poté předány do skutečného objektu COM. Odpovědi z objektu COM jsou směrovány do sestavení vzájemné spolupráce a předány do vaší aplikace .NET Framework.  
  
 Můžete odkazovat na objekt modelu COM bez použití definičního sestavení vložením informací o typu pro objekt modelu COM v sestavení .NET. Chcete-li vložit informace o typu, nastavte vlastnost `Embed Interop Types` na hodnotu `True` pro odkaz na objekt COM. Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte možnost `/link` pro odkaz na knihovnu COM. Další informace naleznete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE). Při práci z příkazového řádku můžete použít nástroj Tlbimp k ručnímu vytváření sestavení vzájemné spolupráce.  
  
### <a name="to-add-references-to-com-objects"></a>Přidání odkazů do objektů COM  
  
1. V nabídce **projekt** zvolte možnost **Přidat odkaz** a potom v dialogovém okně klikněte na kartu **com** .  
  
2. Vyberte součást, kterou chcete použít, ze seznamu objektů COM.  
  
3. Chcete-li zjednodušit přístup k definičnímu sestavení, přidejte příkaz `Imports` na začátek třídy nebo modulu, ve kterém budete používat objekt COM. Například následující příklad kódu importuje obor názvů `INKEDLib` pro objekty, na které se odkazuje v knihovně `Microsoft InkEdit Control 1.0`.  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Vytvoření sestavení vzájemné spolupráce pomocí Tlbimp  
  
1. Přidejte umístění Tlbimp do cesty pro hledání, pokud již není součástí cesty pro hledání a že aktuálně nejste v adresáři, kde je umístěn.  
  
2. Volání Tlbimp z příkazového řádku, který poskytuje následující informace:  
  
    - Název a umístění knihovny DLL, která obsahuje knihovnu typů  
  
    - Název a umístění oboru názvů, kde se mají informace umístit  
  
    - Název a umístění cílového definičního sestavení  
  
     Následující kód poskytuje příklad:  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Pomocí nástroje Tlbimp můžete vytvořit definiční sestavení pro knihovny typů, a to i pro neregistrované objekty COM. Nicméně objekty COM, na které odkazují sestavení interop, musí být správně registrovány v počítači, kde mají být použity. Objekt COM můžete zaregistrovat pomocí nástroje Regsvr32, který je součástí operačního systému Windows.  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
