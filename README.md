ITBench

The ITBench evaluator serves observability data (alerts, metrics, logs, k8s objects, etc.) that were from collected from a real environment during 36 different fault injection scenarios. The purple agent's goal is provide the correct root cause diagnosis and propogation chain for the problem. This diagnosis is then evaluated by an LLM-as-a-judge against the provided ground truth. The metrics of this evaluation are as follows:

    root_cause_entity (precision/recall/F1 + pass@1): Whether the correct root cause entity was identified
    root_cause_entity_k (precision/recall/F1 + pass@1, configurable k): Whether the correct root cause entity was identified in the first k=(1,..,5) model predictions
    root_cause_reasoning: Whether the reasoning for the root cause was correct (0, 0.5 or 1).
    propagation_chain: Scores the full propagation chain
    fault_localization_component_identification: Checks if the model correctly identified the first semantic component to exhibit a significant failure symptom
    root_cause_reasoning_partial: Awards partial credit for reasoning if the model correctly analyzed a downstream symptom when it missed the root cause entity.
    root_cause_proximity (precision/recall/F1): Compute closeness between model root cause entities and the Ground-Truth (GT) root-cause entities based on distance (number of hops) between the model entity’s component and any GT root-cause component
    root_cause_proximity_with_fp (precision/recall/F1): Similar to root_cause_proximity_no_fp but distance is relative to the GT path length


Model Provider and URL for the agent and the evaluator should be set as github repo variables. API Keys should be github repo secrets.
