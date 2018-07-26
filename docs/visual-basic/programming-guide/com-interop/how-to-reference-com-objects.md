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
ms.openlocfilehash: 49f3da396ca5cd48b0cf454ce1ecd5422c28e38f
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199362"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic
V jazyce Visual Basic přidávání odkazů na objekty modelu COM, které mají knihovny typů vyžaduje vytvoření sestavení vzájemné spolupráce pro knihovnu COM. Odkazy na členy objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a pak se předávají do vlastního objektu COM. Odpovědi z objektu modelu COM jsou směrovány na sestavení vzájemné spolupráce a předá vaší [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace.  
  
 Můžete odkazovat na objekt modelu COM bez použití sestavení vzájemné spolupráce s využitím vkládání služby informace o objektu modelu COM typu v sestavení .NET. Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost `True` pro odkaz na objekt modelu COM. Pokud kompilujete pomocí kompilátoru příkazového řádku, použijte `/link` možnost odkazovat na knihovny COM. Další informace najdete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 Visual Basic automaticky vytvoří sestavení vzájemné spolupráce, když přidáte odkaz na knihovnu typů z integrovaného vývojového prostředí (IDE). Při práci z příkazového řádku, můžete použít nástroj Tlbimp můžete ručně vytvořit sestavení vzájemné spolupráce.  
  
### <a name="to-add-references-to-com-objects"></a>Chcete-li přidat odkazy na objekty modelu COM.  
  
1.  Na **projektu** nabídce zvolte **přidat odkaz** a potom klikněte na tlačítko **COM** kartu v dialogovém okně.  
  
2.  Vyberte komponentu, kterou chcete použít v seznamu objektů COM.  
  
3.  Chcete-li zjednodušit přístup ke zprostředkovatelům sestavení, přidejte `Imports` příkaz do horní části třídy nebo modulu, ve které budete používat objekt modelu COM. Například následující příklad importuje obor názvů `INKEDLib` pro objekty, odkazuje `Microsoft InkEdit Control 1.0` knihovny.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Chcete-li vytvořit sestavení vzájemné spolupráce pomocí Tlbimp  
  
1.  Přidejte umístění testovaného Tlbimp do cesty pro hledání, pokud již není součástí cesty pro hledání a nejste momentálně v adresáři, kde se nachází.  
  
2.  Volání Tlbimp z příkazového řádku, zadejte následující informace:  
  
    -   Název a umístění knihovny DLL, která obsahuje knihovny typů  
  
    -   Název a umístění oboru názvů, kde by měl být umístěn informace  
  
    -   Název a umístění cílové sestavení vzájemné spolupráce  
  
     Následující kód představuje příklad:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp slouží k vytvoření sestavení vzájemné spolupráce pro knihovny typů, i pro registrace modelu COM objekty. Objekty COM, na které odkazuje sestavení vzájemné spolupráce ale musí být správně zaregistrovaný, na počítači, kde jsou, který se má použít. Objekt modelu COM lze zaregistrovat pomocí nástroje Regsvr32 zahrnuty s operačním systémem Windows.  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (exportér knihovny typů)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
