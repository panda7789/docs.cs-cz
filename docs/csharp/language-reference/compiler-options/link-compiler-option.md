---
description: -Link (možnosti kompilátoru C#)
title: -Link (možnosti kompilátoru C#)
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
ms.openlocfilehash: 0f6927fd240f3f8535478d163be615fc74dad8d2
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125394"
---
# <a name="-link-c-compiler-options"></a>-Link (možnosti kompilátoru C#)
Způsobí, že kompilátor zpřístupní informace o typu COM v zadaných sestaveních pro projekt, který právě kompilujete.

## <a name="syntax"></a>Syntaxe

```console
-link:fileList
// -or-
-l:fileList
```

## <a name="arguments"></a>Argumenty
 `fileList`  
 Povinná hodnota. Seznam názvů souborů sestavení oddělených čárkami. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.

## <a name="remarks"></a>Poznámky
 `-link`Možnost umožňuje nasadit aplikaci, která obsahuje informace o vloženém typu. Aplikace pak může použít typy v sestavení modulu runtime, které implementuje vložené informace o typu bez nutnosti odkazování na sestavení modulu runtime. Pokud jsou publikovány různé verze sestavení modulu runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat. Příklad naleznete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).

 Použití `-link` Možnosti je zvlášť užitečné, když pracujete se zprostředkovatelem komunikace s objekty com. Můžete vložit typy modelu COM, aby již aplikace nevyžadovala primární definiční sestavení (PIA) v cílovém počítači. `-link`Možnost instruuje kompilátor, aby vložil informace o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaného kódu. Typ COM je identifikovaný hodnotou CLSID (GUID). V důsledku toho může být aplikace spuštěna na cílovém počítači, který má nainstalované stejné typy COM se stejnými hodnotami CLSID. Dobrým příkladem jsou aplikace, které automatizují systém Microsoft Office. Vzhledem k tomu, že aplikace, jako je například Office, obvykle udržují stejnou hodnotu CLSID napříč různými verzemi, může vaše aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalováno .NET Framework 4 nebo novější a vaše aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.

 `-link`Možnost vloží pouze rozhraní, struktury a delegáty. Vkládání tříd modelu COM není podporováno.

> [!NOTE]
> Při vytváření instance vloženého typu modelu COM v kódu, je nutné vytvořit instanci pomocí příslušného rozhraní. Při pokusu o vytvoření instance vloženého typu modelu COM pomocí třídy coclass dojde k chybě.

 Chcete-li nastavit `-link` možnost v aplikaci Visual Studio, přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost na **hodnotu true**. Výchozí hodnota `Embed Interop Types` vlastnosti je **false**.

 Pokud propojíte se sestavením COM (sestavení A), které odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud je splněna jedna z následujících podmínek:

- Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.

- Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.

 Podobně jako u možnosti kompilátoru [-reference](./reference-compiler-option.md) `-link` používá možnost kompilátoru soubor odpovědí CSc. rsp, který odkazuje na často používané .NET Framework sestavení. Pokud nechcete, aby kompilátor používal soubor csc. rsp, použijte možnost kompilátoru [--config](./noconfig-compiler-option.md) .

 Krátká forma `-link` je `-l` .

## <a name="generics-and-embedded-types"></a>Obecné typy a vložené typy
 V následujících částech jsou popsána omezení používání obecných typů v aplikacích, které vkládají typy spolupráce.

### <a name="generic-interfaces"></a>Obecná rozhraní
 Obecná rozhraní, která jsou vložena ze sestavení interop, nelze použít. To je ukázáno v následujícím příkladu.

 [!code-csharp[VbLinkCompilerCS#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#1)]

### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry
 Typy, které mají obecný parametr, jehož typ je vložený ze sestavení vzájemné spolupráce, se nedají použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Zvažte například <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, které je definováno v <xref:Microsoft.Office.Interop.Excel> sestavení. Pokud knihovna vloží typy spolupráce ze <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupní metodu, která vrátí obecný typ s parametrem, jehož typ je <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, musí tato metoda vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.

[!code-csharp[VbLinkCompilerCS#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/utility.cs)]

 V následujícím příkladu kód klienta může zavolat metodu, která vrátí <xref:System.Collections.IList> Obecné rozhraní bez chyby.

 [!code-csharp[VbLinkCompilerCS#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vblinkcompilercs/cs/program.cs#5)]

## <a name="example"></a>Příklad
 Následující kód zkompiluje zdrojový soubor `OfficeApp.cs` a odkazuje na sestavení z `COMData1.dll` a `COMData2.dll` na `OfficeApp.exe` .

```csharp
csc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.cs
```

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md)
- [-Reference (možnosti kompilátoru C#)](./reference-compiler-option.md)
- [-unconfig (možnosti kompilátoru C#)](./noconfig-compiler-option.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](./command-line-building-with-csc-exe.md)
- [Přehled interoperability](../../programming-guide/interop/interoperability-overview.md)
