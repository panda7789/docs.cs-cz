---
title: 'Postupy: odkazování na sestavení se silným názvem'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156475"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Postupy: odkazování na sestavení se silným názvem
Proces pro odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní. Odkaz lze vytvořit buď v době kompilace (počáteční vazba), nebo v době běhu.  
  
K referenci v době kompilace dojde, když označíte kompilátor, že sestavení, které má být zkompilováno, explicitně odkazuje na jiné sestavení. Použijete-li referenční informace při kompilaci, kompilátor automaticky získá veřejný klíč cílového sestavení se silným názvem a umístí jej do odkazu na sestavení zkompilovaného sestavení.
  
> [!NOTE]
> Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by došlo k ohrožení zabezpečení sestavení se silným názvem.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Vytvoření odkazu na sestavení v čase kompilace na sestavení se silným názvem  

Do příkazového řádku zadejte následující příkaz:  

\<*příkaz kompilátoru*>  **/Reference:** \<*název sestavení*>  

V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk, který používáte, a *názvem sestavení* je název odkazovaného sestavení se silným názvem. Můžete také použít další možnosti kompilátoru, jako je například možnost **/t: Library** pro vytvoření sestavení knihovny.  

Následující příklad vytvoří sestavení s názvem *MyAssembly. dll* , které odkazuje na sestavení se silným názvem s názvem *myLibAssembly. dll* z modulu kódu s názvem *MyAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Vytvoření reference za běhu na sestavení se silným názvem  
  
Když vytvoříte odkaz na sestavení se silným názvem, například pomocí metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, je nutné použít zobrazovaný název odkazovaného sestavení se silným názvem. Syntaxe zobrazovaného názvu je následující:  

\<*název sestavení*> **,** \<*číslo verze*> **,** \<*culture*> **,** \<*tokenu veřejného klíče*>  

Příklad:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

V tomto příkladu je `PublicKeyToken` hexadecimální formou tokenu veřejného klíče. Pokud není k dispozici žádná hodnota jazykové verze, použijte `Culture=neutral`.  

Následující příklad kódu ukazuje, jak použít tyto informace s metodou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

Můžete vytisknout hexadecimální formát veřejného klíče a tokenu veřejného klíče pro konkrétní sestavení pomocí následujícího příkazu [silného názvu (Sn. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :  

\<*sestavení* **>** **sn-TP**  

Pokud máte soubor s veřejným klíčem, můžete místo toho použít následující příkaz (Poznamenejte si rozdíl v případě použití možnosti příkazového řádku):  

**sn-tp \<** *soubor veřejného klíče* **>**  

## <a name="see-also"></a>Viz také

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
