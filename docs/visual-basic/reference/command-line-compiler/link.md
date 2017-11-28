---
title: /link (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: effaeae48bdeb1dfd0f8cda31fedf2436e7deaca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="link-visual-basic"></a>/link (Visual Basic)
Způsobí, že kompilátor pro zpřístupnění informací o typu modelu COM v zadaném sestavení pro projekt, který je aktuálně kompilován.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`fileList`|Požadováno. Čárkami oddělený seznam názvů souborů sestavení. Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách.|  
  
## <a name="remarks"></a>Poznámky  
 `/link` Možnost umožňuje nasadit aplikaci, která obsahuje vložené informace o typu. Aplikace pak můžete použít typy v sestavení modulu runtime, které implementují vložené typové informace bez nutnosti odkaz na sestavení modulu runtime. Pokud jsou publikovány v různých verzích sestavení modulu runtime, můžete aplikaci, která obsahuje informace o vložených typu pracovat s různými verzemi bez nutnosti zopakovat. Příklad, naleznete v části [návod: vložení typů ze spravovaných sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Pomocí `/link` možnost je obzvláště užitečná při práci se zprostředkovatel komunikace s objekty COM. Můžete vložit typy modelu COM, tak, aby vaše aplikace vyžaduje již primární spolupracující sestavení (PIA) na cílovém počítači. `/link` Možnost dává pokyn kompilátoru pro vložení informací o typu modelu COM z odkazovaného definičního sestavení do výsledného zkompilovaný kód. Typ modelu COM je identifikována hodnota CLSID (GUID). V důsledku toho lze aplikaci spustit v cílovém počítači, který má nainstalován stejné typy modelu COM pomocí stejné hodnoty CLSID. Dobrým příkladem jsou aplikace, které automatizují Microsoft Office. Vzhledem k tomu, že aplikace, jako je Office obvykle zachovat stejnou hodnotu CLSID mezi různými verzemi, vaše aplikace může použít odkazované typy modelu COM, jak dlouho jako rozhraní .NET Framework 4 nebo novější je nainstalován v cílovém počítači a vaše aplikace používá metody, vlastnosti, nebo události, které jsou součástí odkazované typy modelu COM.  
  
 `/link` Možnost vloží pouze rozhraní, struktur a delegáti. Vložení třídy COM není podporována.  
  
> [!NOTE]
>  Když vytvoříte instanci vloženého typu modelu COM v kódu, musíte vytvořit instanci pomocí odpovídající rozhraní. Při pokusu o vytvoření instance vloženého typu modelu COM pomocí CoClass způsobí chybu.  
  
 Chcete-li nastavit `/link` možnost v [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], přidejte odkaz na sestavení a nastavte `Embed Interop Types` vlastnost, která má **true**. Výchozí hodnota pro `Embed Interop Types` vlastnost je **false**.  
  
 Pokud jste k sestavení modelu COM (sestavení A) které se odkazuje na jiný sestavení modelu COM (sestavení B), budete také muset propojit sestavení B, pokud platí některá z následujících:  
  
-   Typu ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.  
  
-   Pole, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je volána.  
  
 Použití [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.  
  
 Jako [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) – možnost kompilátoru, `/link` používá soubor odpovědí Vbc.rsp, často používanou odkazy [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení. Použít [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) – možnost kompilátoru Pokud nechcete, aby kompilátoru chcete použít soubor Vbc.rsp.  
  
 Zkratka pro `/link` je `/l`.  
  
## <a name="generics-and-embedded-types"></a>Obecné typy a vložené typy.  
 Následující části popisují omezení na použití obecných typů v aplikacích, které přibalit definované typy.  
  
### <a name="generic-interfaces"></a>Obecná rozhraní  
 Obecná rozhraní, které jsou vloženy z definičního sestavení nelze použít. To je ukázáno v následujícím příkladu.  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, které mají obecné parametry  
 Typy, které mají obecný parametr, jehož typ je vložen z definičního sestavení nelze použít, pokud je tento typ z externího sestavení. Toto omezení se nevztahuje na rozhraní. Představte si třeba <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, která je definována v <xref:Microsoft.Office.Interop.Excel> sestavení. Pokud knihovna vkládá typy spolupráce z <xref:Microsoft.Office.Interop.Excel> sestavení a zpřístupňuje je metoda, která vrátí obecný typ, který má parametr, jehož typ <xref:Microsoft.Office.Interop.Excel.Range> rozhraní, že metoda musí vracet generické rozhraní, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 V následujícím příkladu kódu klienta můžete volat metodu, která vrátí <xref:System.Collections.IList> obecné rozhraní bez chyby.  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje zdrojový soubor `OfficeApp.vb` a odkaz na sestavení z `COMData1.dll` a `COMData2.dll` k vytvoření `OfficeApp.exe`.  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Návod: Vložení typů z řízených sestavení](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/ Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [/ Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Úvod do zprostředkovatel komunikace s objekty COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
