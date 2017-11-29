---
title: "Kolekce schématu rozhraní ODBC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 889e84db39af1257d709ef049e18d4397ea700d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="b3d69-102">Kolekce schématu rozhraní ODBC</span><span class="sxs-lookup"><span data-stu-id="b3d69-102">ODBC Schema Collections</span></span>
<span data-ttu-id="b3d69-103">Tato část popisuje podporu kolekci schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="b3d69-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="b3d69-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="b3d69-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="b3d69-105">Ovladač ODBC Microsoft SQL Server podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="b3d69-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b3d69-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="b3d69-106">Tables</span></span>  
  
-   <span data-ttu-id="b3d69-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="b3d69-107">Indexes</span></span>  
  
-   <span data-ttu-id="b3d69-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-108">Columns</span></span>  
  
-   <span data-ttu-id="b3d69-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-109">Procedures</span></span>  
  
-   <span data-ttu-id="b3d69-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b3d69-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b3d69-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b3d69-112">zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b3d69-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-113">Tables and Views</span></span>  
  
|<span data-ttu-id="b3d69-114">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-114">ColumnName</span></span>|<span data-ttu-id="b3d69-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-116">TABLE_CAT</span></span>|<span data-ttu-id="b3d69-117">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-117">String</span></span>|  
|<span data-ttu-id="b3d69-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-118">TABLE_SCHEM</span></span>|<span data-ttu-id="b3d69-119">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-119">String</span></span>|  
|<span data-ttu-id="b3d69-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-120">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-121">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-121">String</span></span>|  
|<span data-ttu-id="b3d69-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-122">TABLE_TYPE</span></span>|<span data-ttu-id="b3d69-123">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-123">String</span></span>|  
|<span data-ttu-id="b3d69-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-124">REMARKS</span></span>|<span data-ttu-id="b3d69-125">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="b3d69-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="b3d69-126">Indexes</span></span>  
  
|<span data-ttu-id="b3d69-127">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-127">ColumnName</span></span>|<span data-ttu-id="b3d69-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-129">TABLE_CAT</span></span>|<span data-ttu-id="b3d69-130">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-130">String</span></span>|  
|<span data-ttu-id="b3d69-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-131">TABLE_SCHEM</span></span>|<span data-ttu-id="b3d69-132">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-132">String</span></span>|  
|<span data-ttu-id="b3d69-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-133">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-134">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-134">String</span></span>|  
|<span data-ttu-id="b3d69-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="b3d69-135">NON_UNIQUE</span></span>|<span data-ttu-id="b3d69-136">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-136">Int16</span></span>|  
|<span data-ttu-id="b3d69-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="b3d69-138">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-138">String</span></span>|  
|<span data-ttu-id="b3d69-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-139">INDEX_NAME</span></span>|<span data-ttu-id="b3d69-140">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-140">String</span></span>|  
|<span data-ttu-id="b3d69-141">TYP</span><span class="sxs-lookup"><span data-stu-id="b3d69-141">TYPE</span></span>|<span data-ttu-id="b3d69-142">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-142">Int16</span></span>|  
|<span data-ttu-id="b3d69-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-144">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-144">Int16</span></span>|  
|<span data-ttu-id="b3d69-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-145">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-146">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-146">String</span></span>|  
|<span data-ttu-id="b3d69-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="b3d69-147">ASC_OR_DESC</span></span>|<span data-ttu-id="b3d69-148">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-148">String</span></span>|  
|<span data-ttu-id="b3d69-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="b3d69-149">CARDINATLITY</span></span>|<span data-ttu-id="b3d69-150">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-150">Int32</span></span>|  
|<span data-ttu-id="b3d69-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-151">PAGES</span></span>|<span data-ttu-id="b3d69-152">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-152">Int32</span></span>|  
|<span data-ttu-id="b3d69-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-153">FILTER_CONDITION</span></span>|<span data-ttu-id="b3d69-154">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-154">String</span></span>|  
|<span data-ttu-id="b3d69-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b3d69-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b3d69-156">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-156">String</span></span>|  
|<span data-ttu-id="b3d69-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-158">Byte</span><span class="sxs-lookup"><span data-stu-id="b3d69-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b3d69-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-159">Columns</span></span>  
  
|<span data-ttu-id="b3d69-160">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-160">ColumnName</span></span>|<span data-ttu-id="b3d69-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-162">TABLE_CAT</span></span>|<span data-ttu-id="b3d69-163">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-163">String</span></span>|  
|<span data-ttu-id="b3d69-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-164">TABLE_SCHEM</span></span>|<span data-ttu-id="b3d69-165">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-165">String</span></span>|  
|<span data-ttu-id="b3d69-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-166">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-167">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-167">String</span></span>|  
|<span data-ttu-id="b3d69-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-168">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-169">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-169">String</span></span>|  
|<span data-ttu-id="b3d69-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-170">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-171">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-171">Int16</span></span>|  
|<span data-ttu-id="b3d69-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-172">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-173">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-173">String</span></span>|  
|<span data-ttu-id="b3d69-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b3d69-174">COLUMN_SIZE</span></span>|<span data-ttu-id="b3d69-175">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-175">Int32</span></span>|  
|<span data-ttu-id="b3d69-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="b3d69-177">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-177">Int32</span></span>|  
|<span data-ttu-id="b3d69-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b3d69-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b3d69-179">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-179">Int16</span></span>|  
|<span data-ttu-id="b3d69-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b3d69-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b3d69-181">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-181">Int16</span></span>|  
|<span data-ttu-id="b3d69-182">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-182">NULLABLE</span></span>|<span data-ttu-id="b3d69-183">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-183">Int16</span></span>|  
|<span data-ttu-id="b3d69-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-184">REMARKS</span></span>|<span data-ttu-id="b3d69-185">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-185">String</span></span>|  
|<span data-ttu-id="b3d69-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b3d69-186">COLUMN_DEF</span></span>|<span data-ttu-id="b3d69-187">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-187">String</span></span>|  
|<span data-ttu-id="b3d69-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-189">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-189">Int16</span></span>|  
|<span data-ttu-id="b3d69-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b3d69-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b3d69-191">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-191">Int16</span></span>|  
|<span data-ttu-id="b3d69-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b3d69-193">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-193">Int32</span></span>|  
|<span data-ttu-id="b3d69-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-195">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-195">Int32</span></span>|  
|<span data-ttu-id="b3d69-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b3d69-196">IS_NULLABLE</span></span>|<span data-ttu-id="b3d69-197">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-197">String</span></span>|  
|<span data-ttu-id="b3d69-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b3d69-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b3d69-199">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-199">String</span></span>|  
|<span data-ttu-id="b3d69-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b3d69-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b3d69-201">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-201">String</span></span>|  
|<span data-ttu-id="b3d69-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-203">Byte</span><span class="sxs-lookup"><span data-stu-id="b3d69-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b3d69-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-204">Procedures</span></span>  
  
|<span data-ttu-id="b3d69-205">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-205">ColumnName</span></span>|<span data-ttu-id="b3d69-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="b3d69-208">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-208">String</span></span>|  
|<span data-ttu-id="b3d69-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b3d69-210">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-210">String</span></span>|  
|<span data-ttu-id="b3d69-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-212">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-212">String</span></span>|  
|<span data-ttu-id="b3d69-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-214">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-214">Int32</span></span>|  
|<span data-ttu-id="b3d69-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-216">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-216">Int32</span></span>|  
|<span data-ttu-id="b3d69-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b3d69-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b3d69-218">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-218">Int32</span></span>|  
|<span data-ttu-id="b3d69-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-219">REMARKS</span></span>|<span data-ttu-id="b3d69-220">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-220">String</span></span>|  
|<span data-ttu-id="b3d69-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b3d69-222">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b3d69-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b3d69-224">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-224">ColumnName</span></span>|<span data-ttu-id="b3d69-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="b3d69-227">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-227">String</span></span>|  
|<span data-ttu-id="b3d69-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b3d69-229">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-229">String</span></span>|  
|<span data-ttu-id="b3d69-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-231">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-231">String</span></span>|  
|<span data-ttu-id="b3d69-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-232">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-233">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-233">String</span></span>|  
|<span data-ttu-id="b3d69-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-234">COLUMN_TYPE</span></span>|<span data-ttu-id="b3d69-235">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-235">Int16</span></span>|  
|<span data-ttu-id="b3d69-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-236">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-237">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-237">Int16</span></span>|  
|<span data-ttu-id="b3d69-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-238">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-239">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-239">String</span></span>|  
|<span data-ttu-id="b3d69-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b3d69-240">COLUMN_SIZE</span></span>|<span data-ttu-id="b3d69-241">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-241">Int32</span></span>|  
|<span data-ttu-id="b3d69-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="b3d69-243">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-243">Int32</span></span>|  
|<span data-ttu-id="b3d69-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b3d69-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b3d69-245">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-245">Int16</span></span>|  
|<span data-ttu-id="b3d69-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b3d69-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b3d69-247">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-247">Int16</span></span>|  
|<span data-ttu-id="b3d69-248">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-248">NULLABLE</span></span>|<span data-ttu-id="b3d69-249">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-249">Int16</span></span>|  
|<span data-ttu-id="b3d69-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-250">REMARKS</span></span>|<span data-ttu-id="b3d69-251">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-251">String</span></span>|  
|<span data-ttu-id="b3d69-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b3d69-252">COLUMN_DEF</span></span>|<span data-ttu-id="b3d69-253">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-253">String</span></span>|  
|<span data-ttu-id="b3d69-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-255">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-255">Int16</span></span>|  
|<span data-ttu-id="b3d69-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b3d69-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b3d69-257">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-257">Int16</span></span>|  
|<span data-ttu-id="b3d69-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b3d69-259">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-259">Int32</span></span>|  
|<span data-ttu-id="b3d69-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-261">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-261">Int32</span></span>|  
|<span data-ttu-id="b3d69-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b3d69-262">IS_NULLABLE</span></span>|<span data-ttu-id="b3d69-263">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-263">String</span></span>|  
|<span data-ttu-id="b3d69-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b3d69-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b3d69-265">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-265">String</span></span>|  
|<span data-ttu-id="b3d69-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b3d69-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b3d69-267">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-267">String</span></span>|  
|<span data-ttu-id="b3d69-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-269">Byte</span><span class="sxs-lookup"><span data-stu-id="b3d69-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b3d69-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b3d69-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b3d69-271">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-271">ColumnName</span></span>|<span data-ttu-id="b3d69-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="b3d69-274">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-274">String</span></span>|  
|<span data-ttu-id="b3d69-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b3d69-276">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-276">String</span></span>|  
|<span data-ttu-id="b3d69-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-278">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-278">String</span></span>|  
|<span data-ttu-id="b3d69-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-279">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-280">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-280">String</span></span>|  
|<span data-ttu-id="b3d69-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-281">COLUMN_TYPE</span></span>|<span data-ttu-id="b3d69-282">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-282">Int16</span></span>|  
|<span data-ttu-id="b3d69-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-283">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-284">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-284">Int16</span></span>|  
|<span data-ttu-id="b3d69-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-285">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-286">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-286">String</span></span>|  
|<span data-ttu-id="b3d69-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b3d69-287">COLUMN_SIZE</span></span>|<span data-ttu-id="b3d69-288">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-288">Int32</span></span>|  
|<span data-ttu-id="b3d69-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="b3d69-290">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-290">Int32</span></span>|  
|<span data-ttu-id="b3d69-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b3d69-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b3d69-292">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-292">Int16</span></span>|  
|<span data-ttu-id="b3d69-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b3d69-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b3d69-294">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-294">Int16</span></span>|  
|<span data-ttu-id="b3d69-295">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-295">NULLABLE</span></span>|<span data-ttu-id="b3d69-296">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-296">Int16</span></span>|  
|<span data-ttu-id="b3d69-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-297">REMARKS</span></span>|<span data-ttu-id="b3d69-298">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-298">String</span></span>|  
|<span data-ttu-id="b3d69-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b3d69-299">COLUMN_DEF</span></span>|<span data-ttu-id="b3d69-300">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-300">String</span></span>|  
|<span data-ttu-id="b3d69-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-302">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-302">Int16</span></span>|  
|<span data-ttu-id="b3d69-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b3d69-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b3d69-304">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-304">Int16</span></span>|  
|<span data-ttu-id="b3d69-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b3d69-306">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-306">Int32</span></span>|  
|<span data-ttu-id="b3d69-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-308">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-308">Int32</span></span>|  
|<span data-ttu-id="b3d69-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b3d69-309">IS_NULLABLE</span></span>|<span data-ttu-id="b3d69-310">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-310">String</span></span>|  
|<span data-ttu-id="b3d69-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="b3d69-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="b3d69-312">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-312">String</span></span>|  
|<span data-ttu-id="b3d69-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="b3d69-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="b3d69-314">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-314">String</span></span>|  
|<span data-ttu-id="b3d69-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-316">Byte</span><span class="sxs-lookup"><span data-stu-id="b3d69-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="b3d69-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="b3d69-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="b3d69-318">Ovladač ODBC Microsoft SQL Server Oracle podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="b3d69-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b3d69-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="b3d69-319">Tables</span></span>  
  
-   <span data-ttu-id="b3d69-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-320">Columns</span></span>  
  
-   <span data-ttu-id="b3d69-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-321">Procedures</span></span>  
  
-   <span data-ttu-id="b3d69-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b3d69-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b3d69-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b3d69-324">zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-324">Views</span></span>  
  
-   <span data-ttu-id="b3d69-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="b3d69-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b3d69-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-326">Tables and Views</span></span>  
  
|<span data-ttu-id="b3d69-327">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-327">ColumnName</span></span>|<span data-ttu-id="b3d69-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-330">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-330">String</span></span>|  
|<span data-ttu-id="b3d69-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-331">TABLE_OWNER</span></span>|<span data-ttu-id="b3d69-332">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-332">String</span></span>|  
|<span data-ttu-id="b3d69-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-333">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-334">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-334">String</span></span>|  
|<span data-ttu-id="b3d69-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-335">TABLE_TYPE</span></span>|<span data-ttu-id="b3d69-336">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-336">String</span></span>|  
|<span data-ttu-id="b3d69-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-337">REMARKS</span></span>|<span data-ttu-id="b3d69-338">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b3d69-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-339">Columns</span></span>  
  
|<span data-ttu-id="b3d69-340">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-340">ColumnName</span></span>|<span data-ttu-id="b3d69-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-343">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-343">String</span></span>|  
|<span data-ttu-id="b3d69-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-344">TABLE_OWNER</span></span>|<span data-ttu-id="b3d69-345">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-345">String</span></span>|  
|<span data-ttu-id="b3d69-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-346">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-347">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-347">String</span></span>|  
|<span data-ttu-id="b3d69-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-348">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-349">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-349">String</span></span>|  
|<span data-ttu-id="b3d69-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-350">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-351">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-351">Int16</span></span>|  
|<span data-ttu-id="b3d69-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-352">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-353">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-353">String</span></span>|  
|<span data-ttu-id="b3d69-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="b3d69-354">PRECISION</span></span>|<span data-ttu-id="b3d69-355">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-355">Int32</span></span>|  
|<span data-ttu-id="b3d69-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="b3d69-356">LENGTH</span></span>|<span data-ttu-id="b3d69-357">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-357">Int32</span></span>|  
|<span data-ttu-id="b3d69-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-358">SCALE</span></span>|<span data-ttu-id="b3d69-359">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-359">Int16</span></span>|  
|<span data-ttu-id="b3d69-360">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="b3d69-360">RADIX</span></span>|<span data-ttu-id="b3d69-361">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-361">Int16</span></span>|  
|<span data-ttu-id="b3d69-362">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-362">NULLABLE</span></span>|<span data-ttu-id="b3d69-363">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-363">Int16</span></span>|  
|<span data-ttu-id="b3d69-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-364">REMARKS</span></span>|<span data-ttu-id="b3d69-365">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-365">String</span></span>|  
|<span data-ttu-id="b3d69-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-367">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b3d69-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-368">Procedures</span></span>  
  
|<span data-ttu-id="b3d69-369">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-369">ColumnName</span></span>|<span data-ttu-id="b3d69-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-372">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-372">String</span></span>|  
|<span data-ttu-id="b3d69-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b3d69-374">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-374">String</span></span>|  
|<span data-ttu-id="b3d69-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-376">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-376">String</span></span>|  
|<span data-ttu-id="b3d69-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-378">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-378">Int16</span></span>|  
|<span data-ttu-id="b3d69-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-380">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-380">Int16</span></span>|  
|<span data-ttu-id="b3d69-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b3d69-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b3d69-382">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-382">Int16</span></span>|  
|<span data-ttu-id="b3d69-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-383">REMARKS</span></span>|<span data-ttu-id="b3d69-384">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-384">String</span></span>|  
|<span data-ttu-id="b3d69-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b3d69-386">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b3d69-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b3d69-388">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-388">ColumnName</span></span>|<span data-ttu-id="b3d69-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-391">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-391">String</span></span>|  
|<span data-ttu-id="b3d69-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b3d69-393">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-393">String</span></span>|  
|<span data-ttu-id="b3d69-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-395">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-395">String</span></span>|  
|<span data-ttu-id="b3d69-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-396">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-397">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-397">String</span></span>|  
|<span data-ttu-id="b3d69-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-398">COLUMN_TYPE</span></span>|<span data-ttu-id="b3d69-399">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-399">Int16</span></span>|  
|<span data-ttu-id="b3d69-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-400">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-401">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-401">Int16</span></span>|  
|<span data-ttu-id="b3d69-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-402">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-403">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-403">String</span></span>|  
|<span data-ttu-id="b3d69-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="b3d69-404">PRECISION</span></span>|<span data-ttu-id="b3d69-405">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-405">Int32</span></span>|  
|<span data-ttu-id="b3d69-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="b3d69-406">LENGTH</span></span>|<span data-ttu-id="b3d69-407">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-407">Int32</span></span>|  
|<span data-ttu-id="b3d69-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-408">SCALE</span></span>|<span data-ttu-id="b3d69-409">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-409">Int16</span></span>|  
|<span data-ttu-id="b3d69-410">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="b3d69-410">RADIX</span></span>|<span data-ttu-id="b3d69-411">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-411">Int16</span></span>|  
|<span data-ttu-id="b3d69-412">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-412">NULLABLE</span></span>|<span data-ttu-id="b3d69-413">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-413">Int16</span></span>|  
|<span data-ttu-id="b3d69-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-414">REMARKS</span></span>|<span data-ttu-id="b3d69-415">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-415">String</span></span>|  
|<span data-ttu-id="b3d69-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-416">OVERLOAD</span></span>|<span data-ttu-id="b3d69-417">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-417">Int32</span></span>|  
|<span data-ttu-id="b3d69-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-419">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="b3d69-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="b3d69-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="b3d69-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce konkrétní schématu kromě běžných kolekcemi schémat:</span><span class="sxs-lookup"><span data-stu-id="b3d69-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="b3d69-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="b3d69-422">Tables</span></span>  
  
-   <span data-ttu-id="b3d69-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="b3d69-423">Indexes</span></span>  
  
-   <span data-ttu-id="b3d69-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-424">Columns</span></span>  
  
-   <span data-ttu-id="b3d69-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-425">Procedures</span></span>  
  
-   <span data-ttu-id="b3d69-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="b3d69-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b3d69-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="b3d69-428">zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="b3d69-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="b3d69-429">Tables and Views</span></span>  
  
|<span data-ttu-id="b3d69-430">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-430">ColumnName</span></span>|<span data-ttu-id="b3d69-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-433">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-433">String</span></span>|  
|<span data-ttu-id="b3d69-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-434">TABLE_OWNER</span></span>|<span data-ttu-id="b3d69-435">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-435">String</span></span>|  
|<span data-ttu-id="b3d69-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-436">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-437">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-437">String</span></span>|  
|<span data-ttu-id="b3d69-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-438">TABLE_TYPE</span></span>|<span data-ttu-id="b3d69-439">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-439">String</span></span>|  
|<span data-ttu-id="b3d69-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-440">REMARKS</span></span>|<span data-ttu-id="b3d69-441">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="b3d69-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="b3d69-442">Columns</span></span>  
  
|<span data-ttu-id="b3d69-443">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-443">ColumnName</span></span>|<span data-ttu-id="b3d69-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-446">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-446">String</span></span>|  
|<span data-ttu-id="b3d69-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-447">TABLE_OWNER</span></span>|<span data-ttu-id="b3d69-448">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-448">String</span></span>|  
|<span data-ttu-id="b3d69-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-449">TABLE_NAME</span></span>|<span data-ttu-id="b3d69-450">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-450">String</span></span>|  
|<span data-ttu-id="b3d69-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-451">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-452">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-452">String</span></span>|  
|<span data-ttu-id="b3d69-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-453">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-454">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-454">Int16</span></span>|  
|<span data-ttu-id="b3d69-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-455">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-456">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-456">String</span></span>|  
|<span data-ttu-id="b3d69-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="b3d69-457">PRECISION</span></span>|<span data-ttu-id="b3d69-458">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-458">Int32</span></span>|  
|<span data-ttu-id="b3d69-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="b3d69-459">LENGTH</span></span>|<span data-ttu-id="b3d69-460">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-460">Int32</span></span>|  
|<span data-ttu-id="b3d69-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-461">SCALE</span></span>|<span data-ttu-id="b3d69-462">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-462">Int16</span></span>|  
|<span data-ttu-id="b3d69-463">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="b3d69-463">RADIX</span></span>|<span data-ttu-id="b3d69-464">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-464">Int16</span></span>|  
|<span data-ttu-id="b3d69-465">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-465">NULLABLE</span></span>|<span data-ttu-id="b3d69-466">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-466">Int16</span></span>|  
|<span data-ttu-id="b3d69-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-467">REMARKS</span></span>|<span data-ttu-id="b3d69-468">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-468">String</span></span>|  
|<span data-ttu-id="b3d69-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-470">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="b3d69-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="b3d69-471">Procedures</span></span>  
  
|<span data-ttu-id="b3d69-472">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-472">ColumnName</span></span>|<span data-ttu-id="b3d69-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-475">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-475">String</span></span>|  
|<span data-ttu-id="b3d69-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b3d69-477">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-477">String</span></span>|  
|<span data-ttu-id="b3d69-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-479">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-479">String</span></span>|  
|<span data-ttu-id="b3d69-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-481">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-481">Int16</span></span>|  
|<span data-ttu-id="b3d69-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="b3d69-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="b3d69-483">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-483">Int16</span></span>|  
|<span data-ttu-id="b3d69-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="b3d69-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="b3d69-485">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-485">Int16</span></span>|  
|<span data-ttu-id="b3d69-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-486">REMARKS</span></span>|<span data-ttu-id="b3d69-487">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-487">String</span></span>|  
|<span data-ttu-id="b3d69-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="b3d69-489">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="b3d69-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="b3d69-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="b3d69-491">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-491">ColumnName</span></span>|<span data-ttu-id="b3d69-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="b3d69-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="b3d69-494">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-494">String</span></span>|  
|<span data-ttu-id="b3d69-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3d69-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="b3d69-496">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-496">String</span></span>|  
|<span data-ttu-id="b3d69-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-498">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-498">String</span></span>|  
|<span data-ttu-id="b3d69-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-499">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-500">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-500">String</span></span>|  
|<span data-ttu-id="b3d69-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-501">COLUMN_TYPE</span></span>|<span data-ttu-id="b3d69-502">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-502">Int16</span></span>|  
|<span data-ttu-id="b3d69-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-503">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-504">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-504">Int16</span></span>|  
|<span data-ttu-id="b3d69-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-505">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-506">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-506">String</span></span>|  
|<span data-ttu-id="b3d69-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="b3d69-507">PRECISION</span></span>|<span data-ttu-id="b3d69-508">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-508">Int32</span></span>|  
|<span data-ttu-id="b3d69-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="b3d69-509">LENGTH</span></span>|<span data-ttu-id="b3d69-510">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-510">Int32</span></span>|  
|<span data-ttu-id="b3d69-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-511">SCALE</span></span>|<span data-ttu-id="b3d69-512">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-512">Int16</span></span>|  
|<span data-ttu-id="b3d69-513">ZÁKLAD –</span><span class="sxs-lookup"><span data-stu-id="b3d69-513">RADIX</span></span>|<span data-ttu-id="b3d69-514">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-514">Int16</span></span>|  
|<span data-ttu-id="b3d69-515">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-515">NULLABLE</span></span>|<span data-ttu-id="b3d69-516">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-516">Int16</span></span>|  
|<span data-ttu-id="b3d69-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-517">REMARKS</span></span>|<span data-ttu-id="b3d69-518">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-518">String</span></span>|  
|<span data-ttu-id="b3d69-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="b3d69-519">OVERLOAD</span></span>|<span data-ttu-id="b3d69-520">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-520">Int32</span></span>|  
|<span data-ttu-id="b3d69-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-522">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="b3d69-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="b3d69-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="b3d69-524">columnName</span><span class="sxs-lookup"><span data-stu-id="b3d69-524">ColumnName</span></span>|<span data-ttu-id="b3d69-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="b3d69-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="b3d69-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="b3d69-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="b3d69-527">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-527">String</span></span>|  
|<span data-ttu-id="b3d69-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="b3d69-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="b3d69-529">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-529">String</span></span>|  
|<span data-ttu-id="b3d69-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="b3d69-531">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-531">String</span></span>|  
|<span data-ttu-id="b3d69-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-532">COLUMN_NAME</span></span>|<span data-ttu-id="b3d69-533">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-533">String</span></span>|  
|<span data-ttu-id="b3d69-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-534">COLUMN_TYPE</span></span>|<span data-ttu-id="b3d69-535">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-535">Int16</span></span>|  
|<span data-ttu-id="b3d69-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-536">DATA_TYPE</span></span>|<span data-ttu-id="b3d69-537">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-537">Int16</span></span>|  
|<span data-ttu-id="b3d69-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="b3d69-538">TYPE_NAME</span></span>|<span data-ttu-id="b3d69-539">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-539">String</span></span>|  
|<span data-ttu-id="b3d69-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="b3d69-540">COLUMN_SIZE</span></span>|<span data-ttu-id="b3d69-541">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-541">Int32</span></span>|  
|<span data-ttu-id="b3d69-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="b3d69-543">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-543">Int32</span></span>|  
|<span data-ttu-id="b3d69-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="b3d69-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="b3d69-545">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-545">Int16</span></span>|  
|<span data-ttu-id="b3d69-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="b3d69-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="b3d69-547">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-547">Int16</span></span>|  
|<span data-ttu-id="b3d69-548">S MOŽNOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="b3d69-548">NULLABLE</span></span>|<span data-ttu-id="b3d69-549">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-549">Int16</span></span>|  
|<span data-ttu-id="b3d69-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="b3d69-550">REMARKS</span></span>|<span data-ttu-id="b3d69-551">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-551">String</span></span>|  
|<span data-ttu-id="b3d69-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="b3d69-552">COLUMN_DEF</span></span>|<span data-ttu-id="b3d69-553">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-553">String</span></span>|  
|<span data-ttu-id="b3d69-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="b3d69-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="b3d69-555">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-555">Int16</span></span>|  
|<span data-ttu-id="b3d69-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="b3d69-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="b3d69-557">Int16</span><span class="sxs-lookup"><span data-stu-id="b3d69-557">Int16</span></span>|  
|<span data-ttu-id="b3d69-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="b3d69-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="b3d69-559">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-559">Int32</span></span>|  
|<span data-ttu-id="b3d69-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="b3d69-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="b3d69-561">Int32</span><span class="sxs-lookup"><span data-stu-id="b3d69-561">Int32</span></span>|  
|<span data-ttu-id="b3d69-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="b3d69-562">IS_NULLABLE</span></span>|<span data-ttu-id="b3d69-563">String</span><span class="sxs-lookup"><span data-stu-id="b3d69-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3d69-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3d69-564">See Also</span></span>  
 [<span data-ttu-id="b3d69-565">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="b3d69-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
