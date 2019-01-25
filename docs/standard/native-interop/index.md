---
title: Nativní interoperabilita – .NET
description: Zjistěte, jak spolupracovat s nativními komponentami v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 29aacc9210b4103f379b7776c36fc3c29b9e6dec
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857616"
---
# <a name="native-interoperability"></a><span data-ttu-id="b7de1-103">Nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b7de1-103">Native interoperability</span></span>

<span data-ttu-id="b7de1-104">Následující články popisují různé způsoby provedení "nativní interoperabilita" v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="b7de1-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="b7de1-105">Existuje několik důvodů, proč byste to provádět volání do nativního kódu:</span><span class="sxs-lookup"><span data-stu-id="b7de1-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="b7de1-106">Operační systémy jsou dostupné velký objem rozhraní API, která nejsou k dispozici v knihoven spravovaných tříd.</span><span class="sxs-lookup"><span data-stu-id="b7de1-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="b7de1-107">Typickým příkladem pro tento scénář bude přístup k hardwaru nebo operačního systému funkce správy.</span><span class="sxs-lookup"><span data-stu-id="b7de1-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="b7de1-108">Komunikace s ostatními součástmi, které máte, nebo můžete vytvořit instrukce ABI ve stylu jazyka C (nativní instrukce ABI), jako je například kód v Javě, který je zveřejněný prostřednictvím [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohla vést nativní součásti.</span><span class="sxs-lookup"><span data-stu-id="b7de1-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="b7de1-109">Na Windows většina softwaru, který se nainstaluje, jako je například sada Microsoft Office, zaregistruje komponenty modelu COM, které představují své programy a vývojářům umožňuje automatizovat je nebo je používat.</span><span class="sxs-lookup"><span data-stu-id="b7de1-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="b7de1-110">Tento proces také vyžaduje nativní interoperabilita.</span><span class="sxs-lookup"><span data-stu-id="b7de1-110">This also requires native interoperability.</span></span>

<span data-ttu-id="b7de1-111">Tento seznam nezahrnuje všechny potenciální situace a scénáře, ve kterých by vývojář chcete/typu/potřeba rozhraní s nativními komponentami.</span><span class="sxs-lookup"><span data-stu-id="b7de1-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="b7de1-112">Knihovna tříd rozhraní .NET, například používá interoperabilitu nativní podporu k implementaci přiměřený počet jejích rozhraní API, jako je podpora konzoly a manipulaci s, přístupu k systému souborů a další.</span><span class="sxs-lookup"><span data-stu-id="b7de1-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="b7de1-113">Je důležité si uvědomit, že je k dispozici možnost v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="b7de1-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="b7de1-114">Většina příkladů v této části se zobrazí pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS).</span><span class="sxs-lookup"><span data-stu-id="b7de1-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="b7de1-115">Ale příklady krátký a příkladů, stačí jeden vzorek je zobrazit, který používá rozšíření (to znamená "knihovny dll" pro knihovny) a názvy souborů Windows.</span><span class="sxs-lookup"><span data-stu-id="b7de1-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="b7de1-116">To neznamená, že tyto funkce nejsou k dispozici v systému Linux nebo macOS, bylo provedeno pouze pro usnadnění práce saké.</span><span class="sxs-lookup"><span data-stu-id="b7de1-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7de1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7de1-117">See also</span></span>

- [<span data-ttu-id="b7de1-118">Vyvolání platformy (nespravovaného)</span><span class="sxs-lookup"><span data-stu-id="b7de1-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="b7de1-119">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="b7de1-119">Type marshalling</span></span>](type-marshalling.md)
- [<span data-ttu-id="b7de1-120">Osvědčené postupy nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b7de1-120">Native interoperability best practices</span></span>](best-practices.md)
