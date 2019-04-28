---
title: 'Postupy: Přepsání logického stromu'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768443"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="5262c-102">Postupy: Přepsání logického stromu</span><span class="sxs-lookup"><span data-stu-id="5262c-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="5262c-103">I když není nutné ve většině případů, pokročilé ovládací prvek Autoři mají možnost přetížení logického stromu.</span><span class="sxs-lookup"><span data-stu-id="5262c-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5262c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5262c-104">Example</span></span>  
 <span data-ttu-id="5262c-105">Tento příklad popisuje, jak podtřídy <xref:System.Windows.Controls.StackPanel> přepsání logického stromu, v tomto případě k vynucení chování, že na panelu může mít jenom a budou vykreslovat pouze jeden podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="5262c-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="5262c-106">To není nezbytně prakticky žádoucí chování, ale je znázorněna zde jako způsob ilustrující scénář pro přepsání elementu normální Logická stromová struktura.</span><span class="sxs-lookup"><span data-stu-id="5262c-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="5262c-107">Další informace o logickém stromu, naleznete v tématu [stromy v subsystému WPF](trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="5262c-107">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>
