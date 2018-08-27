---
title: -link (možnosti kompilátoru C#)
ms.date: 07/20/2015
helpviewer_keywords:
- /l compiler option [C#]
- /link compiler option [C#]
- -l compiler option [C#]
- EmbedInteropTypes
- l compiler option [C#]
- embed interop types [COM Interop]
- -link compiler option [C#]
- link compiler option [C#]
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
ms.openlocfilehash: 668476beb2eefa7a818f60606443ae06ae26a17d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930960"
---
# <a name="-link-c-compiler-options"></a>-link (možnosti kompilátoru C#)
Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Požadováno. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.  
  
## <a name="remarks"></a>Poznámky  
 `-link` Možnost můžete nasazovat aplikace, která obsahuje vložené informace o typu. Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují informace o vloženém typu bez nutnosti odkaz na sestavení modulu runtime. Pokud různé verze sestavení modulu runtime jsou publikovány, aplikace, která obsahuje informace o vloženém typu můžete pracovat se různé verze, aniž byste museli být překompilovány. Příklad najdete v tématu [návod: vložení typů ze spravovaných sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Použití `-link` volba je užitečná při práci se spoluprací COM. Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární definiční sestavení (PIA) na cílovém počítači. `-link` Možnost dává pokyn kompilátoru k vložení informací o typu modelu COM z odkazované sestavení vzájemné spolupráce do výsledné zkompilovaného kódu. Typ modelu COM je identifikován hodnota CLSID (GUID). V důsledku toho může vaše aplikace spouštět na cílovém počítači, který má nainstalovanou stejné typy modelu COM se stejnými hodnotami identifikátoru CLSID. Dobrým příkladem jsou aplikace, které automatizují Microsoft Office. Protože aplikace, jako je Office obvykle ponechat stejnou hodnotu CLSID napříč různými verzemi, aplikace může používat odkazované typy modelu COM v cílovém počítači je nainstalované rozhraní .NET Framework 4 nebo vyšší a vaše aplikace používá metody, vlastnosti, nebo události, které jsou zahrnuty v odkazovaných typů modelu COM.  
  
 `-link` Možnost vloží pouze rozhraní, struktury a delegátů. Vložení třídy modelu COM není podporováno.  
  
> [!NOTE]
>  Při vytváření instance vloženého typu modelu COM ve vašem kódu, musíte vytvořit instanci pomocí odpovídající rozhraní. Pokus o vytvoření instance vloženého typu modelu COM s použitím CoClass způsobí chybu.  
  
 Chcete-li nastavit `-link` v aplikaci Visual Studio, přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost **true**. Výchozí nastavení pro `Embed Interop Types` vlastnost **false**.  
  
 Pokud jste se k sestavení modelu COM (sestavení A) která sama odkazuje na jiné sestavení modelu COM (sestavení B), budete mít taky odkaz na sestavení B, pokud je splněna jedna z následujících akcí:  
  
-   Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.  
  
 Stejně jako [– referenční dokumentace](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru, `-link` – možnost kompilátoru používá Csc.rsp soubor odpovědí, který často používá odkazy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení. Použít [- noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) Pokud nechcete, aby kompilátor, aby používal soubor Csc.rsp – možnost kompilátoru.  
  
 Krátký tvar `-link` je `-l`.  
  
## <a name="generics-and-embedded-types"></a>Obecných typů a vestavěné typy  
 Omezení týkající se použití obecných typů v aplikacích, které vložit typy spolupráce v následujících částech.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry.  
 Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Představme si třeba, <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení. Pokud knihovnu vložené typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrací obecného typu, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 V následujícím příkladu kódu klienta můžete volat metodu, která vrací <xref:System.Collections.IList> obecné rozhraní bez chyb.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód se zkompiluje zdrojový soubor `OfficeApp.cs` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Návod: Vložení typů ze spravovaných sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [-reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [-noconfig (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)
