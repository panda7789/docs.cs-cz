---
title: 'Postup: Odkaz na sestavení se silným názvem'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156475"
---
# <a name="how-to-reference-a-strong-named-assembly"></a>Postup: Odkaz na sestavení se silným názvem
Proces odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní. Můžete provést odkaz buď v době kompilace (brzy vazby) nebo v době běhu.  
  
Odkaz na dobu kompilace dojde, když označíte kompilátoru, že sestavení, které má být kompilován explicitně odkazuje na jiné sestavení. Při použití odkazování v době kompilace kompilátor automaticky získá veřejný klíč cílové sestavení se silným názvem a umístí jej do odkazu sestavení sestavení, které je kompilován.
  
> [!NOTE]
> Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem. V opačném případě by byla ohrožena bezpečnost sestavení se silným názvem.  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a>Vytvořte odkaz na sestavení se silným názvem  

Do příkazového řádku zadejte následující příkaz:  

\<*příkaz*> kompilátoru **/reference:**\<*název sestavení*>  

V tomto příkazu je *příkaz kompilátoru* příkaz kompilátoru pro jazyk, který používáte, a *název sestavení* je název sestavení se silným názvem, na které se odkazuje. Můžete také použít jiné možnosti kompilátoru, jako je například možnost **/t:library** pro vytvoření sestavení knihovny.  

Následující příklad vytvoří sestavení s názvem *myAssembly.dll,* které odkazuje na sestavení se silným názvem s názvem *myLibAssembly.dll* z modulu kódu s názvem *myAssembly.cs*.  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a>Vytvoření odkazu za běhu na sestavení se silným názvem  
  
Při vytvoření odkazu za běhu na sestavení se silným názvem, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> například pomocí metody nebo, musíte použít zobrazovaný název odkazovaného sestavení se silným názvem. Syntaxe zobrazovaného názvu je následující:  

\<*název*>sestavení **,** \< *číslo*>verze **,** \< *jazyková verze*>**,** \<token *veřejného klíče*>  

Například:  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

V tomto `PublicKeyToken` příkladu je šestnáctková forma tokenu veřejného klíče. Pokud neexistuje žádná hodnota `Culture=neutral`jazykové verze, použijte .  

Následující příklad kódu ukazuje, jak používat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> tyto informace s metodou.  

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

Šestnáctkový formát veřejného klíče a tokenveřejného klíče pro konkrétní sestavení můžete vytisknout pomocí následujícího příkazu [Silný název (Sn.exe):](../../framework/tools/sn-exe-strong-name-tool.md)  

**sn \< -Tp** *sestava***>**  

Pokud máte soubor veřejného klíče, můžete místo toho použít následující příkaz (všimněte si rozdílu v případě volby příkazového řádku):  

**sn -tp \< ** *soubor veřejného klíče***>**  

## <a name="see-also"></a>Viz také

- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
