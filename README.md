<?php
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class StoreProduct extends FormRequest
{

 @return bool

public function authorize()
{
return true; 
}

 @return array

public function rules()
{
    return 
    [
        'name' => 'required|string|max:10', 
        'descricao' => 'required|string|max:100',
        'preco' => 'required|integer|min:1',
        'quantidade' => 'required|integer|min:1',
        'disponivel' => 'required|boolean',
        'data_lancamento' => 'required|date',
        'raridade' => 'required|string|in:comum,historica,folclorica',

    ];
}

public function messages()
{
    return [
        'nome.required' => 'O nome do produto é obrigatório.',
        'nome.string' => 'O nome deve ser um texto.',
        'nome.max' => 'O nome não pode ter mais que 255 caracteres.',

        'descricao.string' => 'A descrição deve ser um texto.',
        'descricao.max' => 'A descrição não pode ter mais que 500 caracteres.',

        'preco.required' => 'O preço do produto é obrigatório.',
        'preco.numeric' => 'O preço deve ser um valor numérico.',
        'preco.min' => 'O preço não pode ser negativo.',

        'quantidade.required' => 'A quantidade é obrigatória.',
        'quantidade.integer' => 'A quantidade deve ser um número inteiro.',
        'quantidade.min' => 'A quantidade deve ser pelo menos 1.',

        'disponivel.required' => 'O campo disponibilidade é obrigatório.',
        'disponivel.boolean' => 'O campo disponível deve ser verdadeiro ou falso.',

        'data_lancamento.required' => 'A data de lançamento é obrigatória.',
        'data_lancamento.date' => 'A data de lançamento deve ser uma data válida.',

        'raridade.required' => 'A raridade do produto é obrigatório.',
        'raridade.string' => 'O nome deve ser um texto.',
        'raridade.in' => 'A raridade deve ser uma das seguintes opções: comum, historica ou folclorica.',
    ];
}
}
