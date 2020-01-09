---
title: -link
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
ms.openlocfilehash: c15f55f3a3c2b4e404767ddf96e258bc1e9771d7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716758"
---
# <a name="-link-visual-basic"></a>-Link (Visual Basic)
Způsobí, že kompilátor zpřístupní informace o typu COM v zadaných sestaveních pro projekt, který právě kompilujete.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-link:fileList  
```

nebo  

```console
-l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Požadováno. Seznam názvů souborů sestavení oddělených čárkami. Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-link` umožňuje nasadit aplikaci, která obsahuje informace o vloženém typu. Aplikace pak může použít typy v sestavení modulu runtime, které implementuje vložené informace o typu bez nutnosti odkazování na sestavení modulu runtime. Pokud jsou publikovány různé verze sestavení modulu runtime, aplikace, která obsahuje informace o vloženém typu, může pracovat s různými verzemi, aniž by bylo nutné je znovu zkompilovat. Příklad naleznete v tématu [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md).  
  
 Použití možnosti `-link` je zvlášť užitečné při práci s zprostředkovatelem komunikace s objekty COM. Můžete vložit typy modelu COM, aby již aplikace nevyžadovala primární definiční sestavení (PIA) v cílovém počítači. Možnost `-link` instruuje kompilátor, aby vložil informace o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaného kódu. Typ COM je identifikovaný hodnotou CLSID (GUID). V důsledku toho může být aplikace spuštěna na cílovém počítači, který má nainstalované stejné typy COM se stejnými hodnotami CLSID. Dobrým příkladem jsou aplikace, které automatizují systém Microsoft Office. Vzhledem k tomu, že aplikace, jako je například Office, obvykle udržují stejnou hodnotu CLSID napříč různými verzemi, může vaše aplikace používat odkazované typy COM, pokud je v cílovém počítači nainstalováno .NET Framework 4 nebo novější a vaše aplikace používá metody, vlastnosti nebo události, které jsou zahrnuty v odkazovaných typech COM.  
  
 Možnost `-link` vloží pouze rozhraní, struktury a delegáty. Vkládání tříd modelu COM není podporováno.  
  
> [!NOTE]
> Při vytváření instance vloženého typu modelu COM v kódu, je nutné vytvořit instanci pomocí příslušného rozhraní. Při pokusu o vytvoření instance vloženého typu modelu COM pomocí třídy coclass dojde k chybě.  
  
 Chcete-li nastavit možnost `-link` v sadě Visual Studio, přidejte odkaz na sestavení a nastavte vlastnost `Embed Interop Types` na **hodnotu true**. Výchozí hodnota pro vlastnost `Embed Interop Types` je **false**.  
  
 Pokud propojíte se sestavením COM (sestavení A), které odkazuje na jiné sestavení COM (sestavení B), musíte také propojit se sestavením B, pokud je splněna jedna z následujících podmínek:  
  
- Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
- Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.  
  
 Pomocí [-LIBPATH](libpath.md) Určete adresář, ve kterém je umístěn jeden nebo více odkazů na sestavení.  
  
 Podobně jako u možnosti kompilátoru [-reference](reference.md) používá možnost kompilátoru `-link` soubor odpovědí Vbc. rsp, který odkazuje na často používané .NET Framework sestavení. Pokud nechcete, aby kompilátor používal soubor Vbc. rsp, použijte možnost kompilátoru [--config](noconfig.md) .  
  
 Krátká forma `-link` je `-l`.  
  
## <a name="generics-and-embedded-types"></a>Obecné typy a vložené typy  
 V následujících částech jsou popsána omezení používání obecných typů v aplikacích, které vkládají typy spolupráce.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, která jsou vložena ze sestavení interop, nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry  
 Typy, které mají obecný parametr, jehož typ je vložený ze sestavení vzájemné spolupráce, se nedají použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Zvažte například <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, které je definováno v sestavení <xref:Microsoft.Office.Interop.Excel>. Pokud knihovna vloží typy spolupráce z <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje metodu, která vrátí obecný typ s parametrem, jehož typ je rozhraní <xref:Microsoft.Office.Interop.Excel.Range>, tato metoda musí vracet obecné rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 V následujícím příkladu kód klienta může zavolat metodu, která vrací obecné rozhraní <xref:System.Collections.IList> bez chyby.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příkazový řádek zkompiluje zdrojový soubor `OfficeApp.vb` a referenční sestavení z `COMData1.dll` a `COMData2.dll` k výrobě `OfficeApp.exe`.  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Návod: Vložení typů ze spravovaných sestavení](../../../standard/assembly/embed-types-visual-studio.md)
- [-Reference (Visual Basic)](reference.md)
- [-noconfig](noconfig.md)
- [-libpath](libpath.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Představení zprostředkovatele komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
