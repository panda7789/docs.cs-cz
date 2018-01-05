---
title: "Začínáme (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started [WPF]
- introduction [WPF]
- WPF [WPF], getting started
ms.assetid: 04f91da8-708c-46c7-8172-f1695ec847cd
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b74eafb1189335a642df7cb267727ef7e8ee59b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-wpf"></a><span data-ttu-id="8e279-102">Začínáme (WPF)</span><span class="sxs-lookup"><span data-stu-id="8e279-102">Getting Started (WPF)</span></span>
<span data-ttu-id="8e279-103">Windows Presentation Foundation (WPF) je rozhraní uživatelského rozhraní, které vytvoří klienta pro stolní počítače aplikací.</span><span class="sxs-lookup"><span data-stu-id="8e279-103">Windows Presentation Foundation (WPF) is a UI framework that creates desktop client applications.</span></span> <span data-ttu-id="8e279-104">Vývojové platformy WPF podporuje širokou škálu funkce pro vývoj aplikací, včetně model aplikací, prostředky, ovládací prvky, obrázků, rozložení, datová vazba, dokumenty a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8e279-104">The WPF development platform supports a broad set of application development features, including an application model, resources, controls, graphics, layout, data binding, documents, and security.</span></span> <span data-ttu-id="8e279-105">Je podmnožinu rozhraní .NET Framework, takže pokud jste dříve vytvořili aplikace s rozhraním .NET Framework pomocí technologie ASP.NET nebo Windows Forms, programovací prostředí by mělo být známé.</span><span class="sxs-lookup"><span data-stu-id="8e279-105">It is a subset of the .NET Framework, so if you have previously built applications with the .NET Framework using ASP.NET or Windows Forms, the programming experience should be familiar.</span></span> <span data-ttu-id="8e279-106">K poskytování deklarativní model pro programování aplikací používá WPF Extensible aplikace Markup Language (XAML).</span><span class="sxs-lookup"><span data-stu-id="8e279-106">WPF uses the Extensible Application Markup Language (XAML) to provide a declarative model for application programming.</span></span> <span data-ttu-id="8e279-107">Tato část obsahuje témata, která zavádět a můžete začít pracovat s WPF.</span><span class="sxs-lookup"><span data-stu-id="8e279-107">This section has topics that introduce and help you get started with WPF.</span></span>  
  
## <a name="where-should-i-start"></a><span data-ttu-id="8e279-108">Kde mám začít?</span><span class="sxs-lookup"><span data-stu-id="8e279-108">Where Should I Start?</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e279-109">Chcete rovnou...</span><span class="sxs-lookup"><span data-stu-id="8e279-109">I want to jump right in…</span></span>|[<span data-ttu-id="8e279-110">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="8e279-110">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|  
|<span data-ttu-id="8e279-111">Jak navrhnout aplikace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e279-111">How do I design the application UI?</span></span>|[<span data-ttu-id="8e279-112">Návrh XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8e279-112">Designing XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)|  
|<span data-ttu-id="8e279-113">Aplikací .NET?</span><span class="sxs-lookup"><span data-stu-id="8e279-113">New to .NET?</span></span>|<span data-ttu-id="8e279-114">[Přehled rozhraní .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e279-114">[Overview of the .NET Framework](https://msdn.microsoft.com/en-us/library/zw4w595w\(v=vs.140\).aspx)</span></span><br /><br /> [<span data-ttu-id="8e279-115">Základy vytváření aplikací rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="8e279-115">.NET Framework Application Essentials</span></span>](../../../../docs/standard/application-essentials.md)<br /><br /> <span data-ttu-id="8e279-116">[Začínáme s jazykem Visual C# a Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span><span class="sxs-lookup"><span data-stu-id="8e279-116">[Getting Started with Visual C# and Visual Basic](https://msdn.microsoft.com/en-us/library/dd492171\(v=vs.140\).aspx)</span></span>|  
|<span data-ttu-id="8e279-117">Další informace o WPF...</span><span class="sxs-lookup"><span data-stu-id="8e279-117">Tell me more about WPF…</span></span>|[<span data-ttu-id="8e279-118">Úvod k použití WPF v sadě Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="8e279-118">Introduction to WPF in Visual Studio 2015</span></span>](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)<br /><br /> [<span data-ttu-id="8e279-119">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8e279-119">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)<br /><br /> [<span data-ttu-id="8e279-120">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="8e279-120">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)<br /><br /> [<span data-ttu-id="8e279-121">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="8e279-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)|  
|<span data-ttu-id="8e279-122">Jste vývojář Windows Forms?</span><span class="sxs-lookup"><span data-stu-id="8e279-122">Are you a Windows Forms developer?</span></span>|[<span data-ttu-id="8e279-123">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="8e279-123">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)<br /><br /> [<span data-ttu-id="8e279-124">Vzájemná spolupráce subsystémů WPF a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e279-124">WPF and Windows Forms Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)|  
  
## <a name="see-also"></a><span data-ttu-id="8e279-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e279-125">See Also</span></span>  
 [<span data-ttu-id="8e279-126">Knihovna tříd</span><span class="sxs-lookup"><span data-stu-id="8e279-126">Class Library</span></span>](../../../../docs/framework/wpf/class-library-wpf.md)  
 [<span data-ttu-id="8e279-127">Vývoj aplikací</span><span class="sxs-lookup"><span data-stu-id="8e279-127">Application Development</span></span>](../../../../docs/framework/wpf/app-development/index.md)  
 [<span data-ttu-id="8e279-128">Rozhraní .NET framework Developer Center</span><span class="sxs-lookup"><span data-stu-id="8e279-128">.NET Framework Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=187437)
