---
title: "pomocí statické – direktiva (referenční dokumentace jazyka C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a>pomocí statické – direktiva (referenční dokumentace jazyka C#)

`using static` – Direktiva označí typu jejichž statické členy dostanete bez určení názvu typu. Jeho syntaxe je:

```csharp
using static <fully-qualified-type-name>
```

kde *plně kvalifikovaný typ name* je název typu, jejichž statické členy může být odkazováno bez určení názvu typu. Pokud nezadáte název plně kvalifikovaný typ (název úplné oboru názvů společně s název typu), C# vygeneruje Chyba kompilátoru CS0246: "typu nebo oboru názvů '< typ name >' nebyl nalezen."

`using static` – Direktiva platí pro žádný typ, který má statické členy, i v případě, že má také členů instance. Ale členů instance jde volat jenom pomocí instance typu.

`using static` – Direktiva byla zavedena v C# 6.

## <a name="remarks"></a>Poznámky
 
Normálně při volání je statický člen, zadejte název typu společně s název člena. Opakovaně zadejte přitom stejný název typu pro vyvolání členy typu, může mít za následek podrobné, skrytého kódu. Například následující definice `Circle` třída odkazuje na počet členů <xref:System.Math> třídy.
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

Odstraněním potřeba explicitně odkazovat <xref:System.Math> třídy pokaždé, když se odkazuje člena, `using static` – direktiva vytvoří mnoho čištění kódu:

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

`using static`Importuje pouze přístupné statické členy a vnořené typy, které jsou deklarované v zadaného typu.  Zděděné členy nebyly naimportovány.  Můžete importovat ze všech typů s názvem použití statické direktiva, včetně moduly jazyka Visual Basic.  Pokud funkce vysoké úrovně F # se zobrazí v metadatech jako statické členy s názvem typu, jehož jméno je platný identifikátor C#, lze importovat funkce F #.  
  
 `using static`Díky rozšiřující metody, které jsou deklarované v zadaný typ, který je k dispozici pro rozšíření metoda vyhledávání.  Názvy metod rozšíření však nejsou naimportovány do oboru pro neúplné odkaz v kódu.  
  
 Metody se stejným názvem importovat z různých typů pomocí různých `using static` direktivy v oboru názvů na stejnou jednotku kompilace tvoří skupinu metoda.  Řešení přetížení v rámci těchto skupin metoda odpovídá normální C# pravidla.  
  
## <a name="example"></a>Příklad

Následující příklad používá `using static` – direktiva, aby statické členy <xref:System.Console>, <xref:System.Math>, a <xref:System.String> třídy, které jsou k dispozici bez nutnosti zadávat název jejich typu.

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

V příkladu `using static` – direktiva může také se aplikovaly <xref:System.Double> typu. To by provedli ho lze volat <xref:System.Double.TryParse(System.String,System.Double@)> metoda bez určení názvu typu. To však znamená méně čitelný kód, vzhledem k tomu, že bude nutné zkontrolovat `using static` tvrzení, abyste zjistili, jaké číselného typu `TryParse` metoda je volána.

## <a name="see-also"></a>Viz také

[Using – direktiva](using-directive.md)   
[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)   
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)   
[Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
[Namespace klíčová slova](../../../csharp/language-reference/keywords/namespace-keywords.md)   
[Obory názvů](../../../csharp/programming-guide/namespaces/index.md)   
