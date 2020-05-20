---
title: Modernizaci desktopové aplikace ve Windows 10 s .NET Core 3,1
description: Naučte se modernizovat stávající desktopové aplikace pomocí .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423234"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a><span data-ttu-id="69d5b-103">Modernizaci desktopové aplikace ve Windows 10 s .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="69d5b-103">Modernizing Desktop Apps on Windows 10 with .NET Core 3.1</span></span>

![Snímek obrazovky zobrazující titulní knihu modernizovat desktopových aplikací](./media/modernizing-existing-desktop-apps-ebook-cover.png)

<span data-ttu-id="69d5b-105">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="69d5b-105">PUBLISHED BY</span></span>

<span data-ttu-id="69d5b-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="69d5b-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="69d5b-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="69d5b-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="69d5b-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="69d5b-108">One Microsoft Way</span></span>

<span data-ttu-id="69d5b-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="69d5b-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="69d5b-110">Copyright © 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="69d5b-110">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="69d5b-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="69d5b-111">All rights reserved.</span></span> <span data-ttu-id="69d5b-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="69d5b-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="69d5b-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="69d5b-113">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="69d5b-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="69d5b-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="69d5b-115">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="69d5b-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="69d5b-116">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="69d5b-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="69d5b-117">Microsoft a ochranné známky uvedené na <https://www.microsoft.com> webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69d5b-117">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="69d5b-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="69d5b-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="69d5b-119">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="69d5b-119">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="69d5b-120">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="69d5b-120">Co-Authors:</span></span>

> <span data-ttu-id="69d5b-121">**Olia Gavrysh**, programový manažer, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-121">**Olia Gavrysh**, Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="69d5b-122">**Miguel Angel Castejón Dominguez**, architekt inovace, kabel</span><span class="sxs-lookup"><span data-stu-id="69d5b-122">**Miguel Angel Castejón Dominguez**, Innovation Architect, Kabel</span></span>

<span data-ttu-id="69d5b-123">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="69d5b-123">Participants and reviewers:</span></span>

> <span data-ttu-id="69d5b-124">**Maira Wenzel**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-124">**Maira Wenzel**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="69d5b-125">**Andy de Gorge**, náměstek – vývojář obsahu, tým docs pro .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-125">**Andy De Gorge**, Senior Content Developer, .NET docs team, Microsoft</span></span>

> <span data-ttu-id="69d5b-126">**Miguel Ramos**, vedoucí program pro vývoj aplikací, tým vývojářů platformy Windows, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-126">**Miguel Ramos**, Senior Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="69d5b-127">**Adam Braden**, hlavní správce programů, tým pro vývojáře Windows Developer Platform, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-127">**Adam Braden**, Principal Program Manager, Windows Developer Platform team, Microsoft</span></span>

> <span data-ttu-id="69d5b-128">**Ricardo Minguez Pablos**, vedoucí program, tým Azure IoT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-128">**Ricardo Minguez Pablos**, Senior Program Manager, Azure IoT team, Microsoft</span></span>

> <span data-ttu-id="69d5b-129">**Nish Anil**, vedoucí program, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-129">**Nish Anil**, Senior Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="69d5b-130">**Beth Massi**, vedoucí marketing pro produkty, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-130">**Beth Massi**, Senior Product Marketing Manager, Microsoft</span></span>

> <span data-ttu-id="69d5b-131">**Scott Hunterem**, správce programu partnera pro partnery, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="69d5b-131">**Scott Hunter**, Partner Director Program Manager, .NET team, Microsoft</span></span>

> <span data-ttu-id="69d5b-132">**Marta Fuentes Lara**, kabel</span><span class="sxs-lookup"><span data-stu-id="69d5b-132">**Marta Fuentes Lara**, Kabel</span></span>

> <span data-ttu-id="69d5b-133">**Raúl Fernández de Córdoba**; kabel</span><span class="sxs-lookup"><span data-stu-id="69d5b-133">**Raúl Fernández de Córdoba**, Kabel</span></span>

> <span data-ttu-id="69d5b-134">**Antonio Manuel Fernández Cantos**, kabel</span><span class="sxs-lookup"><span data-stu-id="69d5b-134">**Antonio Manuel Fernández Cantos**, Kabel</span></span>

## <a name="introduction"></a><span data-ttu-id="69d5b-135">Úvod</span><span class="sxs-lookup"><span data-stu-id="69d5b-135">Introduction</span></span>

<span data-ttu-id="69d5b-136">Tato kniha obsahuje informace o strategiích, které můžete použít k přesunutí stávajících aplikací klasické pracovní plochy prostřednictvím cesty k modernizaci a začlenit nejnovější funkce pro modul runtime, jazyk a platformu.</span><span class="sxs-lookup"><span data-stu-id="69d5b-136">This book is about strategies you can adopt to move your existing desktop applications through the path of modernization and incorporate the latest runtime, language, and platform features.</span></span> <span data-ttu-id="69d5b-137">Zjistíte, že neexistuje žádný jedinečný recept, protože každá aplikace je odlišná, a proto jsou vaše požadavky a předvolby.</span><span class="sxs-lookup"><span data-stu-id="69d5b-137">You'll discover that there's no unique recipe as each application is different, and so are your requirements and preferences.</span></span> <span data-ttu-id="69d5b-138">Dobrá zpráva je, že existují běžné přístupy, které můžete použít k přidání nových funkcí a možností do aplikací.</span><span class="sxs-lookup"><span data-stu-id="69d5b-138">The good news is that there are common approaches you can apply to add new features and capabilities to your applications.</span></span> <span data-ttu-id="69d5b-139">Některé z nich ani nevyžadují významné změny kódu.</span><span class="sxs-lookup"><span data-stu-id="69d5b-139">Some of them won't even require major modifications of your code.</span></span> <span data-ttu-id="69d5b-140">V této knize si ukážeme, jak všechny tyto funkce fungují na pozadí a vysvětlují mechanismy jejich implementace.</span><span class="sxs-lookup"><span data-stu-id="69d5b-140">In this book, we'll reveal how all those features work behind the scenes and explain the mechanics of their implementations.</span></span> <span data-ttu-id="69d5b-141">Kromě toho najdete některé běžné scénáře pro modernizaci existující aplikace klasické pracovní plochy, takže můžete najít inspiraci pro vývoj vašich projektů.</span><span class="sxs-lookup"><span data-stu-id="69d5b-141">Moreover, you'll find some common scenarios for modernizing existing desktop applications shown in detail so you can find inspiration for evolving your projects.</span></span>

<span data-ttu-id="69d5b-142">Přístup Microsoftu k modernizaci stávajících aplikací vám poskytne flexibilitu při vytváření vlastní přizpůsobené cesty.</span><span class="sxs-lookup"><span data-stu-id="69d5b-142">Microsoft's approach to modernizing existing applications is to give you the flexibility to create your own customized path.</span></span> <span data-ttu-id="69d5b-143">Všechny strategie pro moderní navýšení popsané v této příručce jsou většinou nezávislé.</span><span class="sxs-lookup"><span data-stu-id="69d5b-143">All the modernization strategies described in this book are mostly independent.</span></span> <span data-ttu-id="69d5b-144">Můžete vybrat ty, které jsou relevantní pro vaši aplikaci, a přeskočit jiné, které pro vás nejsou důležité.</span><span class="sxs-lookup"><span data-stu-id="69d5b-144">You can choose ones that are relevant for your application and skip others that aren't important for you.</span></span> <span data-ttu-id="69d5b-145">Jinými slovy, můžete vzájemně kombinovat a odpovídat strategiím, které vašim potřebám vaší aplikace nejlépe vyřešíte.</span><span class="sxs-lookup"><span data-stu-id="69d5b-145">In other words, you can mix and match the strategies to best address your application needs.</span></span>

## <a name="who-should-use-the-book"></a><span data-ttu-id="69d5b-146">Kdo má knihu používat</span><span class="sxs-lookup"><span data-stu-id="69d5b-146">Who should use the book</span></span>

<span data-ttu-id="69d5b-147">Tuto knihu jsme napsali pro vývojáře a architekty řešení, kteří chtějí modernizovat stávající desktopové aplikace model Windows Forms a WPF a využívat výhody .NET Core a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="69d5b-147">We wrote this book for developers and solution architects who want to modernize existing Windows Forms and WPF desktop applications to leverage the benefits of .NET Core and Windows 10.</span></span>

<span data-ttu-id="69d5b-148">Tuto příručku můžete také najít užitečnou, pokud jste Tvůrce technického rozhodnutí, jako je například podnikový architekt nebo vedoucí vývoj nebo ředitel, který chce získat přehled o výhodách aktualizace existujících aplikací klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="69d5b-148">You might also find this book useful if you're a technical decision maker, such as an enterprise architect or a development lead or director who wants an overview of the benefits of updating existing desktop applications.</span></span>

## <a name="how-to-use-the-book"></a><span data-ttu-id="69d5b-149">Jak používat knihu</span><span class="sxs-lookup"><span data-stu-id="69d5b-149">How to use the book</span></span>

<span data-ttu-id="69d5b-150">Tato kniha obsahuje vysvětlení "Proč", proč byste mohli chtít modernizovat své stávající aplikace a konkrétní výhody, které získáte pomocí .NET Core 3,1 a MSIX pro modernizovat aplikací klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="69d5b-150">This book addresses the "why"—why you might want to modernize your existing applications, and the specific benefits you get from using NET Core 3.1 and MSIX to modernize your desktop apps.</span></span> <span data-ttu-id="69d5b-151">Obsah knihy je navržený pro architekty a pracovníky technického rozhodování, kteří chtějí mít přehled, ale nepotřebují se soustředit na implementaci a technický krok, podrobné informace.</span><span class="sxs-lookup"><span data-stu-id="69d5b-151">The content of the book is designed for architects and technical decision makers who want an overview, but who don't need to focus on implementation and technical, step-by-step details.</span></span>

<span data-ttu-id="69d5b-152">V různých kapitolách jsou k dispozici ukázkové fragmenty kódu implementace a snímky obrazovky, přičemž kapitola 5 nabízí kompletní proces migrace pro ukázkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="69d5b-152">Along the different chapters, sample implementation code snippets and screenshots are provided, with chapter 5 devoted to showcase a complete migration process for sample applications.</span></span>

## <a name="what-this-book-doesnt-cover"></a><span data-ttu-id="69d5b-153">Co tato kniha nepokrývá</span><span class="sxs-lookup"><span data-stu-id="69d5b-153">What this book doesn't cover</span></span>

<span data-ttu-id="69d5b-154">Tato kniha se zabývá konkrétní podmnožinou scénářů, které se zaměřují na scénáře navýšení a posunutí, a vysvětluje způsob, jak získat výhody modernizaci bez snahy o přepis kódu.</span><span class="sxs-lookup"><span data-stu-id="69d5b-154">This book covers a specific subset of scenarios that are focused on lift-and-shift scenarios, outlining the way to gain the benefits of modernizing without the effort of rewriting code.</span></span>

<span data-ttu-id="69d5b-155">Tato kniha nemá informace o vývoji moderních aplikací s využitím zcela nového .NET Core nebo o zahájení práce s model Windows Forms a WPF.</span><span class="sxs-lookup"><span data-stu-id="69d5b-155">This book isn't about developing modern applications with .NET Core from scratch or about getting started with Windows Forms and WPF.</span></span> <span data-ttu-id="69d5b-156">Zaměřuje se na to, jak můžete aktualizovat existující aplikace klasické pracovní plochy s využitím nejnovějších technologií pro vývoj desktopových aplikací.</span><span class="sxs-lookup"><span data-stu-id="69d5b-156">It focuses on how you can update existing desktop applications with the latest technologies for desktop development.</span></span>

## <a name="samples-used-in-this-book"></a><span data-ttu-id="69d5b-157">Ukázky používané v této knize</span><span class="sxs-lookup"><span data-stu-id="69d5b-157">Samples used in this book</span></span>

<span data-ttu-id="69d5b-158">K zdůraznění nezbytných kroků pro provedení modernizace budeme používat ukázkovou aplikaci s názvem `eShopModernizing` .</span><span class="sxs-lookup"><span data-stu-id="69d5b-158">To highlight the necessary steps to perform a modernization, we'll be using a sample application called `eShopModernizing`.</span></span> <span data-ttu-id="69d5b-159">Tato aplikace má dva typy, model Windows Forms a WPF, a my vám ukážeme podrobný postup, jak provést modernizaci na obou těchto počítačích pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="69d5b-159">This application has two flavors, Windows Forms and WPF, and we'll show a step-by-step process on how to perform the modernization on both of them to .NET Core.</span></span>

<span data-ttu-id="69d5b-160">V úložišti GitHub pro tuto knihu najdete také výsledky procesu, pomocí kterých se můžete rozhodnout, jestli se rozhodnete postupovat podle podrobného kurzu.</span><span class="sxs-lookup"><span data-stu-id="69d5b-160">Also, on the GitHub repository for this book, you'll find the results of the process, which you can consult with if you decide to follow the step-by-step tutorial.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="69d5b-161">Poslat svůj názor</span><span class="sxs-lookup"><span data-stu-id="69d5b-161">Send your feedback</span></span>

<span data-ttu-id="69d5b-162">Tato kniha a související ukázky se neustále vyvíjí, takže se vaše zpětná vazba vítá!</span><span class="sxs-lookup"><span data-stu-id="69d5b-162">This book and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="69d5b-163">Pokud máte komentáře k tomu, jak se tato kniha dá zlepšit, použijte část zpětná vazba v dolní části každé stránky založené na [problémech na GitHubu](https://github.com/dotnet/docs/issues).</span><span class="sxs-lookup"><span data-stu-id="69d5b-163">If you have comments about how this book can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="69d5b-164">Další</span><span class="sxs-lookup"><span data-stu-id="69d5b-164">Next</span></span>](why-modern-applications.md)
