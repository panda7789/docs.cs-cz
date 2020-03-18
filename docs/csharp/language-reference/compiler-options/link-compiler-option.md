---
title: -link (Možnosti kompilátoru Jazyka C#)
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
ms.openlocfilehash: 4c96f7be5ac500886ea036c93b4651fa814ee58a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970098"
---
# <a name="-link-c-compiler-options"></a>-link (Možnosti kompilátoru Jazyka C#)
Způsobí, že kompilátor zpřístupnit informace o typu COM v zadaných sestaveních projektu, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-link:fileList  
// -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
 `fileList`  
 Povinná hodnota. Seznam názvů souborů sestavení oddělených čárkami. Pokud název souboru obsahuje mezeru, uzavřete jej do uvozovek.  
  
## <a name="remarks"></a>Poznámky  
 Tato `-link` možnost umožňuje nasadit aplikaci, která má vložené informace o typu. Aplikace pak můžete použít typy v sestavení za běhu, které implementují informace o vloženém typu bez nutnosti odkazu na sestavení za běhu. Pokud jsou publikovány různé verze sestavení runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat. Příklad najdete [v tématu Návod: Vkládání typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).  
  
 Použití `-link` této možnosti je užitečné zejména při práci s komop. Typy COM můžete vložit tak, aby aplikace již nevyžadovala primární sestavení interop (PIA) v cílovém počítači. Tato `-link` možnost instruuje kompilátor vložit informace o typu COM z odkazované ho sestavení interop do výsledného kompilovaného kódu. Typ COM je identifikován hodnotou CLSID (GUID). V důsledku toho může být aplikace spuštěna v cílovém počítači, který nainstaloval stejné typy COM se stejnými hodnotami CLSID. Dobrým příkladem jsou aplikace, které automatizují sadu Microsoft Office. Vzhledem k tomu, že aplikace, jako je Office, obvykle zachovávaly stejnou hodnotu CLSID v různých verzích, může aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalována rozhraní .NET Framework 4 nebo novější a aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.  
  
 Možnost `-link` vloží pouze rozhraní, struktury a delegáty. Vkládání tříd COM není podporováno.  
  
> [!NOTE]
> Při vytváření instance vloženého typu COM v kódu je nutné vytvořit instanci pomocí příslušného rozhraní. Pokus o vytvoření instance vloženého typu COM pomocí třídy CoClass způsobí chybu.  
  
 Chcete-li `-link` nastavit možnost v sadě Visual Studio, přidejte odkaz na sestavení a nastavte vlastnost na `Embed Interop Types` **hodnotu true**. Výchozí hodnota `Embed Interop Types` vlastnosti je **false**.  
  
 Pokud propojíte sestavení COM (sestavení A), které samo odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud platí některá z následujících podmínek:  
  
- Typ z sestavení A dědí z typu nebo implementuje rozhraní z sestavení B.  
  
- Pole, vlastnost, událost nebo metoda, která má návratový typ nebo typ parametru z sestavení B je vyvolána.  
  
 Stejně jako možnost kompilátoru `-link` [-reference](./reference-compiler-option.md) používá možnost kompilátoru soubor odpovědí Csc.rsp, který odkazuje na často používaná sestavení rozhraní .NET Framework. Pokud nechcete, aby kompilátor používal soubor Csc.rsp, použijte možnost kompilátoru [-noconfig.](./noconfig-compiler-option.md)  
  
 Krátká forma `-link` je `-l`.  
  
## <a name="generics-and-embedded-types"></a>Obecné typy a vložené typy  
 Následující části popisují omezení používání obecných typů v aplikacích, které vkládají typy interop.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, která jsou vložena z interop sestavení nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry  
 Typy, které mají obecný parametr, jehož typ je vložen z interop sestavení nelze použít, pokud tento typ je z externího sestavení. Toto omezení se nevztahuje na rozhraní. Zvažte například <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, které <xref:Microsoft.Office.Interop.Excel> je definováno v sestavení. Pokud knihovna vloží interop <xref:Microsoft.Office.Interop.Excel> typy z sestavení a zpřístupní metodu, která vrací <xref:Microsoft.Office.Interop.Excel.Range> obecný typ, který má parametr, jehož typ je rozhraní, tato metoda musí vrátit obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#2)]  
[!code-csharp[VbLinkCompilerCS#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#3)]  
[!code-csharp[VbLinkCompilerCS#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs#4)]  
  
 V následujícím příkladu může klientský kód <xref:System.Collections.IList> volat metodu, která vrací obecné rozhraní bez chyby.  
  
 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový `OfficeApp.cs` soubor a referenční sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.  
  
```csharp  
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md)
- [-reference (Možnosti kompilátoru Jazyka C#)](./reference-compiler-option.md)
- [-noconfig (Možnosti kompilátoru Jazyka C#)](./noconfig-compiler-option.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](./command-line-building-with-csc-exe.md)
- [Přehled interoperability](../../programming-guide/interop/interoperability-overview.md)
