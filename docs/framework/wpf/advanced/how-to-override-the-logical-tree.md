---
title: 'Postupy: Přetížení logického stromu'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: 0c7269b9ea052019e2e4f6def23b063903cbb5e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542887"
---
# <a name="how-to-override-the-logical-tree"></a><span data-ttu-id="8b5b4-102">Postupy: Přetížení logického stromu</span><span class="sxs-lookup"><span data-stu-id="8b5b4-102">How to: Override the Logical Tree</span></span>
<span data-ttu-id="8b5b4-103">Ačkoli to není nezbytné ve většině případů, ovládacího prvku rozšířené autorům mít možnost přepsání logickém stromu.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-103">Although it is not necessary in most cases, advanced control authors have the option to override the logical tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b5b4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b5b4-104">Example</span></span>  
 <span data-ttu-id="8b5b4-105">Tento příklad popisuje postup podtřídami <xref:System.Windows.Controls.StackPanel> k přepsání logickém stromu. v takovém případě vynutit chování, že panelu může mít pouze a učiní pouze jeden podřízený element.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-105">This example describes how to subclass <xref:System.Windows.Controls.StackPanel> to override the logical tree, in this case to enforce a behavior that the panel may only have and will only render a single child element.</span></span> <span data-ttu-id="8b5b4-106">To není nezbytně prakticky žádoucí chování, ale zobrazí se zde jako prostředek ilustrující tento scénář pro přepsání elementu normální logickém stromu.</span><span class="sxs-lookup"><span data-stu-id="8b5b4-106">This isn't necessarily a practically desirable behavior, but is shown here as a means of illustrating the scenario for overriding an element's normal logical tree.</span></span>  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 <span data-ttu-id="8b5b4-107">Další informace o logickém stromu najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="8b5b4-107">For more information on the logical tree, see [Trees in WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).</span></span>
