---
title: Nativní interoperabilita - .NET
description: Přečtěte si, jak komunikovat s nativními součástmi v rozhraní .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706332"
---
# <a name="native-interoperability"></a><span data-ttu-id="2f683-103">Nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="2f683-103">Native interoperability</span></span>

<span data-ttu-id="2f683-104">Následující články ukazují různé způsoby provedení "nativní interoperability" v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2f683-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="2f683-105">Existuje několik důvodů, proč byste chtěli volat do nativního kódu:</span><span class="sxs-lookup"><span data-stu-id="2f683-105">There are a few reasons why you'd want to call into native code:</span></span>

- <span data-ttu-id="2f683-106">Operační systémy jsou dodávány s velkým objemem api, které nejsou k dispozici v knihovnách spravovaných tříd.</span><span class="sxs-lookup"><span data-stu-id="2f683-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="2f683-107">Ukázkovým příkladem tohoto scénáře by byl přístup k funkcím správy hardwaru nebo operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2f683-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
- <span data-ttu-id="2f683-108">Komunikace s jinými součástmi, které mají nebo mohou vytvářet ABIs ve stylu C (nativní abis), jako je například kód Java, který je vystaven prostřednictvím [nativního rozhraní Java (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) nebo jiného spravovaného jazyka, který by mohl vytvořit nativní součást.</span><span class="sxs-lookup"><span data-stu-id="2f683-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
- <span data-ttu-id="2f683-109">V systému Windows většina softwaru, který je nainstalován, například sada Microsoft Office, registruje komponenty modelu COM, které představují jejich programy, a umožňuje vývojářům je automatizovat nebo používat.</span><span class="sxs-lookup"><span data-stu-id="2f683-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="2f683-110">To také vyžaduje nativní interoperabilitu.</span><span class="sxs-lookup"><span data-stu-id="2f683-110">This also requires native interoperability.</span></span>

<span data-ttu-id="2f683-111">Předchozí seznam nepokrývá všechny potenciální situace a scénáře, ve kterých by vývojář chtěl/ rád / potřeboval rozhraní s nativními součástmi.</span><span class="sxs-lookup"><span data-stu-id="2f683-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="2f683-112">Knihovna tříd .NET například používá nativní podporu interoperability k implementaci slušného počtu svých rozhraní API, jako je podpora a manipulace konzoly, přístup k systému souborů a další.</span><span class="sxs-lookup"><span data-stu-id="2f683-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="2f683-113">Je však důležité si uvědomit, že v případě potřeby existuje možnost.</span><span class="sxs-lookup"><span data-stu-id="2f683-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="2f683-114">Většina příkladů v této části bude prezentována pro všechny tři podporované platformy pro .NET Core (Windows, Linux a macOS).</span><span class="sxs-lookup"><span data-stu-id="2f683-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="2f683-115">U některých krátkých a ilustrativních příkladů je však zobrazena pouze jedna ukázka, která používá názvy souborů systému Windows a rozšíření (tj. "dll" pro knihovny).</span><span class="sxs-lookup"><span data-stu-id="2f683-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="2f683-116">To neznamená, že tyto funkce nejsou k dispozici na Linuxu nebo macOS, bylo to provedeno pouze pro pohodlí.</span><span class="sxs-lookup"><span data-stu-id="2f683-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f683-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f683-117">See also</span></span>

- [<span data-ttu-id="2f683-118">Vyvolání platformy (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="2f683-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="2f683-119">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="2f683-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="2f683-120">Nativní osvědčené postupy interoperability</span><span class="sxs-lookup"><span data-stu-id="2f683-120">Native interoperability best practices</span></span>](best-practices.md)
