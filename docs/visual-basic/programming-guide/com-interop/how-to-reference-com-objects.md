---
title: 'Postupy: Objekty odkaz modelu COM z jazyka Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 0327c497025630747e526503556f4a1705948850
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295260"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Postupy: Objekty odkaz modelu COM z jazyka Visual Basic
V jazyce Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM. Odkazy na členy objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a pak se předávají do vlastního objektu COM. Odpovědi z objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a předá vaší [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace.  
  
 Můžete odkazovat na objekt modelu COM bez použití sestavení vzájemné spolupráce s využitím vkládání služby informace o objektu modelu COM typu v sestavení .NET. Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost `True` pro odkaz na objekt modelu COM. Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte `/link` možnost odkazovat na knihovny COM. Další informace najdete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE). Při práci z příkazového řádku, můžete použít nástroj Tlbimp můžete ručně vytvořit sestavení vzájemné spolupráce.  
  
### <a name="to-add-references-to-com-objects"></a>Chcete-li přidat odkazy na objekty modelu COM.  
  
1. Na **projektu** nabídce zvolte **přidat odkaz** a potom klikněte na tlačítko **COM** kartu v dialogovém okně.  
  
2. Vyberte komponentu, kterou chcete použít v seznamu objektů COM.  
  
3. Chcete-li zjednodušit přístup ke zprostředkovatelům sestavení, přidejte `Imports` příkaz do horní části třídy nebo modulu, ve které budete používat objekt modelu COM. Například následující příklad importuje obor názvů `INKEDLib` pro objekty, odkazuje `Microsoft InkEdit Control 1.0` knihovny.  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Chcete-li vytvořit sestavení vzájemné spolupráce pomocí Tlbimp  
  
1. Přidejte umístění testovaného Tlbimp do cesty pro hledání, pokud již není součástí cesty pro hledání a nejste momentálně v adresáři, kde se nachází.  
  
2. Volání Tlbimp z příkazového řádku, zadejte následující informace:  
  
    -   Název a umístění knihovny DLL, která obsahuje knihovny typů  
  
    -   Název a umístění oboru názvů, kde by měl být umístěn informace  
  
    -   Název a umístění cílové sestavení vzájemné spolupráce  
  
     Následující kód představuje příklad:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp slouží k vytvoření sestavení vzájemné spolupráce pro knihovny typů, i pro registrace modelu COM objekty. Objekty COM, na které odkazuje sestavení vzájemné spolupráce ale musí být správně zaregistrovaný, na počítači, kde jsou, který se má použít. Objekt modelu COM lze zaregistrovat pomocí nástroje Regsvr32 zahrnuty s operačním systémem Windows.  
  
## <a name="see-also"></a>Viz také:

- [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)
- [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportér knihovny typů)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
