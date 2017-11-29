---
title: "Cílení na rozhraní .NET Framework 2.0 v systému Windows 8"
description: "Informace o cílení na starší verzi rozhraní .NET Framework, při použití F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63989543-95c3-4ab7-81f3-3834a8b15010
ms.openlocfilehash: 2c0191267da5bee7b844c11cdee168ccfb3321c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="targeting-older-versions-of-net"></a><span data-ttu-id="0cf75-104">Cílení na starší verze rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="0cf75-104">Targeting Older Versions of .NET</span></span>

> [!NOTE]
<span data-ttu-id="0cf75-105">V tomto článku není aktuální pomocí nejnovější sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cf75-105">This article is not up to date with the latest Visual Studio.</span></span>  <span data-ttu-id="0cf75-106">Bude aktualizována.</span><span class="sxs-lookup"><span data-stu-id="0cf75-106">It will be updated.</span></span>

<span data-ttu-id="0cf75-107">Může objevit následující chyba, pokud se pokusíte rozhraní .NET Framework 2.0, 3.0 nebo 3.5 v F # projektu při instalaci sady Visual Studio na Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="0cf75-107">The following error might appear if you try to target the .NET Framework 2.0, 3.0, or 3.5 in an F# project when Visual Studio is installed on Windows 8.1:</span></span> 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

<span data-ttu-id="0cf75-108">Tato chyba se označuje dojde za následující kombinace podmínky:</span><span class="sxs-lookup"><span data-stu-id="0cf75-108">This error is known to occur under the following combination of conditions:</span></span>


- <span data-ttu-id="0cf75-109">Visual Studio nainstalujete na Windows 8.1.</span><span class="sxs-lookup"><span data-stu-id="0cf75-109">You installed Visual Studio on Windows 8.1.</span></span>
<br />

- <span data-ttu-id="0cf75-110">Před instalací sady Visual Studio je nebyla povolit rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="0cf75-110">You didn’t enable the .NET Framework 3.5 before you installed Visual Studio.</span></span>
<br />

- <span data-ttu-id="0cf75-111">Cílem vašeho projektu je .NET Framework 2.0, 3.0 nebo 3.5.</span><span class="sxs-lookup"><span data-stu-id="0cf75-111">Your project targets the .NET Framework 2.0, 3.0, or 3.5.</span></span>
<br />

<span data-ttu-id="0cf75-112">Při instalaci sady Visual Studio, zjistí nainstalovaných verzí rozhraní .NET Framework a pouze v případě, že rozhraní .NET Framework 3.5 je nainstalované a povolené nainstaluje 2.0 Runtime F #.</span><span class="sxs-lookup"><span data-stu-id="0cf75-112">When you install Visual Studio, it detects the installed versions of the .NET Framework and installs the F# 2.0 Runtime only if the .NET Framework 3.5 is installed and enabled.</span></span>


## <a name="resolving-the-error"></a><span data-ttu-id="0cf75-113">Řešení chyby</span><span class="sxs-lookup"><span data-stu-id="0cf75-113">Resolving the Error</span></span>
<span data-ttu-id="0cf75-114">Chcete-li tuto chybu vyřešit, můžete buď cílový novější verzi rozhraní .NET Framework, nebo můžete povolit rozhraní .NET Framework 3.5 ve Windows 8.1 a pak nainstalovat modul runtime F # 2.0 spuštěním instalačního programu pro sadu Visual Studio s **Repair** možnost.</span><span class="sxs-lookup"><span data-stu-id="0cf75-114">To resolve this error, you can either target a newer version of the .NET Framework, or you can enable the .NET Framework 3.5 on Windows 8.1 and then install the F# 2.0 runtime by running the setup program for Visual Studio with the **Repair** option.</span></span>


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a><span data-ttu-id="0cf75-115">Chcete-li povolit rozhraní .NET Framework 3.5 ve Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="0cf75-115">To enable the .NET Framework 3.5 on Windows 8.1</span></span>

1. <span data-ttu-id="0cf75-116">Na **spustit** obrazovky, začnete-li zadat **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="0cf75-116">On the **Start** screen, start to enter **Control Panel**.</span></span>
<br />  <span data-ttu-id="0cf75-117">Jako zadáte název, **ovládací panely** ikonu se zobrazí pod **aplikace** záhlaví.</span><span class="sxs-lookup"><span data-stu-id="0cf75-117">As you enter that name, the **Control Panel** icon appears under the **Apps** heading.</span></span>
<br />

2. <span data-ttu-id="0cf75-118">Vyberte **ovládací panely** ikonu, vyberte **programy** ikonu a potom zvolte **Windows zapnout nebo vypnout funkce** odkaz.</span><span class="sxs-lookup"><span data-stu-id="0cf75-118">Choose the **Control Panel** icon, choose the **Programs** icon, and then choose the **Turn Windows features on or off** link.</span></span>
<br />

3. <span data-ttu-id="0cf75-119">Ujistěte se, že **rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a 3.0)** zaškrtávací políčko je zaškrtnuto a potom vyberte **OK** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0cf75-119">Make sure that the **.NET Framework 3.5 (includes .NET 2.0 and 3.0)** check box is selected, and then choose the **OK** button.</span></span>
<br />  <span data-ttu-id="0cf75-120">Nemusíte zaškrtněte políčka pro všechny podřízené uzly pro volitelné součásti rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0cf75-120">You don’t need to select the check boxes for any child nodes for optional components of the .NET Framework.</span></span>
<br />  <span data-ttu-id="0cf75-121">Rozhraní .NET Framework 3.5 je povoleno, pokud ji už nebyl.</span><span class="sxs-lookup"><span data-stu-id="0cf75-121">The .NET Framework 3.5 is enabled if it wasn't already.</span></span>
<br />


#### <a name="to-install-the-f-20-runtime"></a><span data-ttu-id="0cf75-122">Chcete-li nainstalovat modul runtime F # 2.0</span><span class="sxs-lookup"><span data-stu-id="0cf75-122">To install the F# 2.0 runtime</span></span>

1. <span data-ttu-id="0cf75-123">V Ovládacích panelech, vyberte **programy** propojit a potom zvolte **programy a funkce** odkaz.</span><span class="sxs-lookup"><span data-stu-id="0cf75-123">In the Control Panel, choose the **Programs** link, and then choose the **Programs and Features** link.</span></span>
<br />

2. <span data-ttu-id="0cf75-124">V seznamu nainstalovaných programů, vyberte edice sady Visual Studio, který jste nainstalovali a potom zvolte **změnu** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0cf75-124">In the list of installed programs, choose the edition of Visual Studio that you installed, and then choose the **Change** button.</span></span>
<br />

3. <span data-ttu-id="0cf75-125">Po spuštění instalace, klikněte **Repair** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0cf75-125">After setup starts, choose the **Repair** button.</span></span>
<br />  <span data-ttu-id="0cf75-126">Další informace najdete v tématu [instalaci sady Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span><span class="sxs-lookup"><span data-stu-id="0cf75-126">For more information, see [Installing Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).</span></span>
<br />
## <a name="see-also"></a><span data-ttu-id="0cf75-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cf75-127">See Also</span></span>
[<span data-ttu-id="0cf75-128">Visual F #</span><span class="sxs-lookup"><span data-stu-id="0cf75-128">Visual F#</span></span>](../index.md)
