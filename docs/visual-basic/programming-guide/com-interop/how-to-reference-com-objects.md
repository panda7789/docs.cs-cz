---
title: 'Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 2e2cbac6fad5e1686b7383c44619b8c6f5326483
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396801"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic
V Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů, vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM. Odkazy na členy objektu COM jsou směrovány do sestavení vzájemné spolupráce a poté předány do skutečného objektu COM. Odpovědi z objektu COM jsou směrovány do sestavení vzájemné spolupráce a předány do vaší aplikace .NET Framework.  
  
 Můžete odkazovat na objekt modelu COM bez použití definičního sestavení vložením informací o typu pro objekt modelu COM v sestavení .NET. Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost na hodnotu `True` pro odkaz na objekt modelu COM. Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte `/link` možnost pro odkazování na knihovnu com. Další informace najdete v tématu [-Link (Visual Basic)](../../reference/command-line-compiler/link.md).  
  
 Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE). Při práci z příkazového řádku můžete použít nástroj Tlbimp k ručnímu vytváření sestavení vzájemné spolupráce.  
  
### <a name="to-add-references-to-com-objects"></a>Přidání odkazů do objektů COM  
  
1. V nabídce **projekt** zvolte možnost **Přidat odkaz** a potom v dialogovém okně klikněte na kartu **com** .  
  
2. Vyberte součást, kterou chcete použít, ze seznamu objektů COM.  
  
3. Chcete-li zjednodušit přístup k definičnímu sestavení, přidejte `Imports` příkaz na začátek třídy nebo modulu, ve kterém budete používat objekt com. Například následující příklad kódu importuje obor názvů `INKEDLib` pro objekty, na které je odkazováno v `Microsoft InkEdit Control 1.0` knihovně.  
  
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
  
## <a name="see-also"></a>Viz také

- [Zprostředkovatel komunikace s objekty COM](index.md)
- [Tlbimp. exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp. exe (Exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Řešení potíží s interoperabilitou](troubleshooting-interoperability.md)
- [Imports – příkaz (obor názvů a typ rozhraní .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
