---
title: "-link (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 229bd7e6a7f3691bcb4e6c6dab6f9f36dc3d45f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="link-c-compiler-options"></a>/link (Možnosti kompilátoru C#)
Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
 `fileList`  
 Požadováno. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách.  
  
## <a name="remarks"></a>Poznámky  
 `/link` Možnost umožňuje nasadit aplikaci, která obsahuje vložené informace o typu. Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují vložené typové informace bez nutnosti odkaz na sestavení modulu runtime. Pokud jsou publikovány v různých verzích sestavení modulu runtime, můžete aplikaci, která obsahuje informace o vložených typu pracovat s různými verzemi bez nutnosti zopakovat. Příklad, naleznete v části [návod: vložení typů ze spravovaných sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).  
  
 Pomocí `/link` možnost je obzvláště užitečná při práci se zprostředkovatel komunikace s objekty COM. Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární spolupracující sestavení (PIA) na cílovém počítači. `/link` Možnost dává pokyn kompilátoru pro vložení informací o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaný kód. Typ modelu COM je identifikována hodnota CLSID (GUID). V důsledku toho lze aplikaci spustit v cílovém počítači, který má nainstalován stejné typy modelu COM pomocí stejné hodnoty CLSID. Dobrým příkladem jsou aplikace, které automatizují Microsoft Office. Vzhledem k tomu, že aplikace, jako je Office obvykle zachovat stejnou hodnotu CLSID mezi různými verzemi, vaše aplikace může použít odkazované typy modelu COM, jak dlouho jako rozhraní .NET Framework 4 nebo novější je nainstalován v cílovém počítači a vaše aplikace používá metody, vlastnosti, nebo události, které jsou součástí odkazované typy modelu COM.  
  
 `/link` Možnost vloží pouze rozhraní, struktur a delegáti. Vložení třídy COM není podporována.  
  
> [!NOTE]
>  Když vytvoříte instanci vloženého typu modelu COM v kódu, musíte vytvořit instanci pomocí odpovídající rozhraní. Při pokusu o vytvoření instance vloženého typu modelu COM pomocí CoClass způsobí chybu.  
  
 Chcete-li nastavit `/link` možnost v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost, která má **true**. Výchozí hodnota pro `Embed Interop Types` vlastnost je **false**.  
  
 Pokud jste k sestavení modelu COM (sestavení A) které se odkazuje na jiný sestavení modelu COM (sestavení B), budete také muset propojit sestavení B, pokud platí některá z následujících:  
  
-   Typu ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Pole, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je volána.  
  
 Podobně jako [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) – možnost kompilátoru, `/link` – možnost kompilátoru používá Csc.rsp soubor odpovědí, který odkazuje na často používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení. Použít [/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) – možnost kompilátoru Pokud nechcete, aby kompilátor používal soubor Csc.rsp.  
  
 Zkratka pro `/link` je `/l`.  
  
## <a name="generics-and-embedded-types"></a>Obecné typy a vložené typy.  
 Následující části popisují omezení na použití obecných typů v aplikacích, které přibalit definované typy.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-csharp[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry  
 Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Představte si třeba <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení. Pokud knihovna vkládá typy spolupráce z <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrátí obecný typ, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet generické rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-csharp[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-csharp[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-csharp[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 V následujícím příkladu kódu klienta můžete volat metodu, která vrátí <xref:System.Collections.IList> obecné rozhraní bez chyby.  
  
 [!code-csharp[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `OfficeApp.cs` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.  
  
```csharp  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Návod: Vložení typů z řízených sestavení](../../programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/ Reference (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)  
 [/ noconfig (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)  
 [Sestavování pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Přehled interoperability](../../../csharp/programming-guide/interop/interoperability-overview.md)
