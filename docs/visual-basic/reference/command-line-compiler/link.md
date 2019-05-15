---
title: -link (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: b13d8266d0702d831a0f5ebb3a9586864fe22ccb
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586526"
---
# <a name="-link-visual-basic"></a>-link (Visual Basic)
Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Povinný parametr. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.|  
  
## <a name="remarks"></a>Poznámky  
 `-link` Možnost můžete nasazovat aplikace, která obsahuje vložené informace o typu. Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují informace o vloženém typu bez nutnosti odkaz na sestavení modulu runtime. Pokud různé verze sestavení modulu runtime jsou publikovány, aplikace, která obsahuje informace o vloženém typu můžete pracovat se různé verze, aniž byste museli být překompilovány. Příklad najdete v tématu [názorný postup: Vložení typů ze spravovaných sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).  
  
 Použití `-link` volba je užitečná při práci se spoluprací COM. Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární definiční sestavení (PIA) na cílovém počítači. `-link` Možnost dává pokyn kompilátoru k vložení informací o typu modelu COM z odkazované sestavení vzájemné spolupráce do výsledné zkompilovaného kódu. Typ modelu COM je identifikován hodnota CLSID (GUID). V důsledku toho může vaše aplikace spouštět na cílovém počítači, který má nainstalovanou stejné typy modelu COM se stejnými hodnotami identifikátoru CLSID. Dobrým příkladem jsou aplikace, které automatizují Microsoft Office. Protože aplikace, jako je Office obvykle ponechat stejnou hodnotu CLSID napříč různými verzemi, aplikace může používat odkazované typy modelu COM v cílovém počítači je nainstalované rozhraní .NET Framework 4 nebo vyšší a vaše aplikace používá metody, vlastnosti, nebo události, které jsou zahrnuty v odkazovaných typů modelu COM.  
  
 `-link` Možnost vloží pouze rozhraní, struktury a delegátů. Vložení třídy modelu COM není podporováno.  
  
> [!NOTE]
>  Při vytváření instance vloženého typu modelu COM ve vašem kódu, musíte vytvořit instanci pomocí odpovídající rozhraní. Pokus o vytvoření instance vloženého typu modelu COM s použitím CoClass způsobí chybu.  
  
 Chcete-li nastavit `-link` v aplikaci Visual Studio, přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost **true**. Výchozí nastavení pro `Embed Interop Types` vlastnost **false**.  
  
 Pokud jste se k sestavení modelu COM (sestavení A) která sama odkazuje na jiné sestavení modelu COM (sestavení B), budete mít taky odkaz na sestavení B, pokud je splněna jedna z následujících akcí:  
  
- Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.  
  
- Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.  
  
 Použití [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.  
  
 Stejně jako [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru, `-link` – možnost kompilátoru používá Vbc.rsp soubor odpovědí, který se odkazuje na často používané sestavení rozhraní .NET Framework. Použít [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) Pokud nechcete, aby kompilátor používal soubor Vbc.rsp – možnost kompilátoru.  
  
 Krátký tvar `-link` je `-l`.  
  
## <a name="generics-and-embedded-types"></a>Obecných typů a vestavěné typy  
 Omezení týkající se použití obecných typů v aplikacích, které vložit typy spolupráce v následujících částech.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry.  
 Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Představme si třeba, <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení. Pokud knihovnu vložené typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrací obecného typu, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 V následujícím příkladu kódu klienta můžete volat metodu, která vrací <xref:System.Collections.IList> obecné rozhraní bez chyb.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příkaz zkompiluje zdrojový soubor `OfficeApp.vb` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Návod: Vložení typů ze spravovaných sestavení](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [– referenční dokumentace (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Představení zprostředkovatele komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
