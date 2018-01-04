---
title: 'Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a8ac167b40688b1d1116f148d0d5fd6afdcaada8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Postupy: Odkaz na objekty modelu COM z jazyka Visual Basic
V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], přidávání odkazů na objekty modelu COM, které mají knihovny typů vyžaduje vytvoření spolupráce sestavení pro knihovny COM. Odkazy na členy objektu COM jsou směrovány do sestavení vzájemné spolupráce a předá ji vlastního objektu COM. Odpovědí z objektu COM jsou směrovány do sestavení vzájemné spolupráce a předávaných do vaší [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] aplikace.  
  
 Objekt modelu COM bez použití zprostředkovatele komunikace s objekty sestavení vložení informací o typu objektu COM v sestavení rozhraní .NET, můžete odkazovat. Chcete-li vložit informace o typu, nastavte `Embed Interop Types` vlastnost `True` pro odkaz na objekt COM. Pokud jste se kompilace pomocí kompilátoru příkazového řádku, použijte `/link` možnost, chcete-li knihovny COM. Další informace najdete v tématu [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Když přidáte odkaz na knihovnu typů z integrované vývojové prostředí (IDE) automaticky vytvoří spolupráce – sestavení. Při práci z příkazového řádku, můžete použít nástroj Tlbimp ručně vytvořit sestavení vzájemné spolupráce.  
  
### <a name="to-add-references-to-com-objects"></a>Chcete-li přidat odkazy na objekty modelu COM  
  
1.  Na **projektu** nabídce zvolte **přidat odkaz na** a pak klikněte na tlačítko **COM** karta v dialogovém okně.  
  
2.  Vyberte komponentu, kterou chcete použít v seznamu objektů COM.  
  
3.  Zjednodušení přístupu k sestavení vzájemné spolupráce, přidejte `Imports` příkaz do horní části třídy nebo modul, ve které budete používat objekt COM. Například následující příklad kódu importuje obor názvů `INKEDLib` pro objekty v odkazuje `Microsoft InkEdit Control 1.0` knihovny.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Chcete-li vytvořit pomocí Tlbimp sestavení spolupráce  
  
1.  Přidejte umístění Tlbimp do cesty k vyhledávání, pokud již není součástí cesta hledání a nejste aktuálně v adresáři, kde se nachází.  
  
2.  Volání Tlbimp z příkazového řádku, poskytuje následující informace:  
  
    -   Název a umístění knihovny DLL, která obsahuje knihovny typů  
  
    -   Název a umístění oboru názvů, kde má být umístěn informace  
  
    -   Název a umístění cíl sestavení spolupráce  
  
     Následující kód představuje příklad:  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp slouží k vytvoření spolupráce – sestavení pro knihovny typů, i pro zrušení registrace COM – objekty. Objekty COM, na kterou odkazuje sestavení vzájemné spolupráce však musí být správně zaregistrován, na počítači, kde mají být použity. Objekt modelu COM můžete zaregistrovat pomocí nástroje Regsvr32 součástí operačního systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importér knihovny typů)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (exportér knihovny typů)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Návod: Implementace dědičnosti pomocí objektů COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Řešení potíží s interoperabilitou](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
